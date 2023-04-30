<template>
  <div class="home" >
    <FilterTask></FilterTask>
    <div v-for="post in posts">
      <TaskCards :key="post.id" :task="post" @RefreshDone="refreshData" @remove="removeHandler"></TaskCards>
    </div>

  </div>
</template>

<script>
// @ is an alias to /src
import TaskCards from "../components/TaskCards.vue"
import FilterTask from "../components/FilterTaks.vue"
// import addTask from "../components/AddTask.vue"
export default {
  name: 'HomeView',
  components: { TaskCards, FilterTask },
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
    },


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
</style>
