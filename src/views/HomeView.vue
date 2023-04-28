<template>
  <div class="home">

    <div v-for="post in posts">
      <TaskCards  :key="post.id" :task="post"  @RefreshDone="refreshData"></TaskCards>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import TaskCards from "../components/TaskCards.vue"
export default {
  name: 'HomeView',
  components: { TaskCards },
  data() {
    return {
      url: "http://localhost:3000/posts",
      posts:[]

    }
  },
  methods: {
    refreshData(id){
      let findTask=this.posts.find(item =>  item.id == id )
      // console.log(findTask)
      findTask.complated = !findTask.complated
      // console.log(findTask.complated)
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
</style>
