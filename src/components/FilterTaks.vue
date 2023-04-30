  <template>
  <div>
    <div class="items">
      <RouterLink to="/addTask">
        <span class="material-symbols-outlined addItem">
          add_circle
        </span>
      </RouterLink>
      <div>
        <button class="buttons" @click="filterHandler('complated')">complated</button>
        <button class="buttons" @click="filterHandler('uncomplated')">uncomplated</button>
        <button class="buttons" @click="filterHandler('all')">all</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FilterTaks",

  methods: {
    filterHandler(value) {
      this.$emit("filter",value)
    }
  }
}
</script>

<style  scoped>
.buttons {
  padding: 10px;
  margin: 5px;
  width: 100px;
  border-radius: 10px;
  border: none;
  outline: none;
  box-shadow: 2px 2px 5px #535452;

  animation: 3s ease-in all;
}

.addItem {
  color: red;
  font-size: 2.3rem;
}

.buttons:hover {
  background-color: greenyellow;
  color: red;
}

.items {
  display: flex;
  justify-content: space-between;
  flex-direction: row-reverse;
}
</style>
