<template>
  <div class="home">
    <FilterTask @filter="filterHandler"></FilterTask>
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
      posts: [],
      constPosts: []

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
    filterHandler(value) {
      switch (value) {
        case "all":
          fetch(this.url)
            .then(res => res.json())
            .then(data => { this.posts = data, this.constPosts = data })
            .catch(error => console.log(error))
          break;
        case "complated":
          const ComplatedPost = this.constPosts.filter(item => item.complated == true)
          this.posts = ComplatedPost
          break;
        case "uncomplated":
          const unComplatedPost = this.constPosts.filter(item => item.complated == false)
          this.posts = unComplatedPost
          break
        default:
          console.log("nothing")
          break;
      }
    }


  },
  mounted() {
    fetch(this.url)
      .then(res => res.json())
      .then(data => { this.posts = data, this.constPosts = data })
      .catch(error => console.log(error))

  },


}
</script>
<style scoped>
.home {
  width: 500px;
}
</style>
