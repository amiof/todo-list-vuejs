<template>
  <div>
    <div class="items">
      <RouterLink to="/addTask">
        <span class="material-symbols-outlined addItem">
          add_circle
        </span>
      </RouterLink>
      <div>
        <button class="buttons">complated</button>
        <button class="buttons">uncomplated</button>
        <button class="buttons">all</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FilterTaks",

}
</script>

<style  scoped>
.buttons {
  padding: 10px;
  margin: 5px;
  width: 100px;
  border-radius: 10px;
  box-shadow: 2px 2px 5px #535452;
  animation: 3s ease-in all;
}

.addItem {
  color: red;
  font-size: 2.3rem;
}

.buttons:hover {
  background-color: #f56c14;
  color: white;
}

.items {
  display: flex;
  justify-content: space-between;
  flex-direction: row-reverse;
}
</style>
