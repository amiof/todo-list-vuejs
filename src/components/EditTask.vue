<template>
  <div class="container">
    <h1>edit Task</h1>
    <div class="inputData">
      <label name="input">task: </label>
      <input type="text" v-model="taskTitle" />
      <div class="textArea">
        <label name="details">details:</label>
        <textarea v-model="taskDetails"></textarea>
      </div>
    </div>
    <button @click="submitHandler">edit task</button>
  </div>
</template>

<script>
export default {
  name: "EditTask",
  props: ["id"],
  data() {
    return {
      taskTitle: "",
      taskDetails: "",
      url: "http://localhost:3000/posts/" + this.id,
    }
  },
  methods: {
    submitHandler(){
      const editedData={
        title:this.taskTitle,
        body:this.taskDetails
      }
      fetch(this.url,{
        method:"PATCH",
        headers:{"content-type":"application/json"},
        body:JSON.stringify(editedData) 
      }).then(()=>this.$router.push("/"))
      .catch(error=>console.log(error.message))
    }
  },
  mounted() {
    fetch(this.url).then(res => res.json())
    // .then(data=>console.log(data))
      .then(data => {
        this.taskTitle = data.title,
        this.taskDetails = data.body
      })
    .catch(error=>console.log(error))
  },
}
</script>

<style  scoped>
h1 {
  padding: 30px;
  color: red;
}

input {
  padding: 10px;
  outline: none;
  border: none;
  border-radius: 10px;
  font-size: 1.3rem;
}

.container {
  background-color: #f0f0f0;
  border-radius: 20px;
  box-shadow: 5px 5px 20px gray;
}

.inputData {
  display: flex;
  flex-direction: column;
  margin: 50px
}

.textArea {
  display: flex;
  flex-direction: column;
  margin-top: 50px;
  /* border: 1px solid black; */
}

label {
  text-align: start;
  margin: 10px;
  font-size: 1.5rem;
  color: #969796;

}


textarea {
  width: 400px;
  height: 300px;
  padding: 10px;
  font-size: 1.5rem;
  border: none;
  border-radius: 30px;

}

button {
  padding: 10px;
  margin-bottom: 10px;
  background-color: red;
  color: white;
  cursor: pointer;
  border-radius: 10px;
}

button:hover {

  background-color: green;
}
</style>
