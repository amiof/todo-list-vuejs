<template>
  <div class="container">
    <h1>add Task</h1>
    <div class="inputData">
      <label name="input">task: </label>
      <input type="text" />
      <div class="textArea">
        <label name="details">details:</label>
        <textarea></textarea>
      </div>
    </div>
    <button>submit</button>
  </div>
</template>

<script>
export default {
  name: "AddTask"

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
