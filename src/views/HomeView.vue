<template>
  <div class="home">
    <div class="items">
      <RouterLink to="/addTask">
        <span class="material-symbols-outlined">
          add_circle
        </span>
      </RouterLink>
      <div>
        <button class="buttons">complated</button>
        <button class="buttons">uncomplated</button>
        <button class="buttons">all</button>
      </div>
    </div>
    <div v-for="post in posts">
      <TaskCards :key="post.id" :task="post" @RefreshDone="refreshData" @remove="removeHandler"></TaskCards>
    </div>

  </div>
</template>

<script>
// @ is an alias to /src
import TaskCards from "../components/TaskCards.vue"
// import addTask from "../components/AddTask.vue"
export default {
  name: 'HomeView',
  components: { TaskCards },
  data() {
    return {
      url: "http://localhost:3000/posts",
      posts: []

    }
  },
  methods: {
    refreshData(id) {
      let findTask = this.posts.find(item => item.id == id)
      // console.log(findTask)
      findTask.complated = !findTask.complated
      // console.log(findTask.complated)
    },
    removeHandler(id) {
      const filteredData = this.posts.filter(item => item.id !== id)
      this.posts = filteredData
    }
  },
  mounted() {
    fetch(this.url)
      .then(res => res.json())
      .then(data => this.posts = data)
      .catch(error => console.log(error))

  },


}
</script>
<style scoped>
.home {
  width: 500px;
}

.buttons {
  padding: 10px;
  margin: 5px;
  width: 100px;
  border-radius: 10px;
  box-shadow: 2px 2px 5px #535452;
  animation: 3s ease-in all ;
}

.buttons:hover {
  background-color: #1fdb09;
  color: white;
}

.items {
  display: flex;
  justify-content: space-between;
  flex-direction: row-reverse;
}
</style>
