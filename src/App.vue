<template>
  <div id="app">
    <img src="./assets/saturnanimation.gif">
    <router-view/>
  </div>

</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
body {
  margin: 0;
  background-color: rgb(221, 224, 199);
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

img {
  border-radius: 2em;
  box-shadow: 5px 10px 8px #888888;
}
</style>
