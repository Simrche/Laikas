<template>
<section id="container">
  <div id="sidebarApp">
    <Sidebar/>
  </div>
  <div id="application">
    <Chrono/>
  </div>
</section>


</template>

<script>
import Chrono from './components/Chrono.vue'
import Sidebar from './components/Sidebar.vue'

export default {
  name: 'App',
  components: {
    Sidebar,
    Chrono
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 50px auto;
  width: 80%;
}

#container {
  display: flex;
  justify-content: space-around;
}

#sidebarApp {
  width: 20%;
  background-color: red;
  padding-bottom: 100px;
}

#application {
  width: 70%;
  background-color: blue;
  padding-bottom: 100px;
}
</style>
