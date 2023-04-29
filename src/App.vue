<template>
  <!-- <nav> -->
  <!--   <router-link to="/">Home</router-link> | -->
  <!--   <router-link to="/about">About</router-link> -->
  <!-- </nav> -->
  <h1 class="title">todo list </h1>
  <router-view />
</template>

<style>
body {
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0px;
  padding: 0px;
  background: linear-gradient(90deg, hsla(201, 100%, 64%, 1) 0%, hsla(117, 64%, 64%, 1) 100%);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.title {
  color: white;
  margin-bottom: 50px;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
