<template>
<section id="container">
  <div id="sidebarApp">
    <Sidebar @minu='minu' @chrono='go'/>
  </div>
  <div id="application">
    <Chrono v-if="chrono" @chrono='go'/>
    <Minuteur v-if="minuteur"/>
  </div>
</section>


</template>

<script>
import Chrono from './components/Chrono.vue'
import Minuteur from './components/Minuteur.vue'
import Sidebar from './components/Sidebar.vue'

export default {
  name: 'App',
  components: {
    Sidebar,
    Chrono,
    Minuteur
  },
  data() {
      return {
        chrono: true,
        minuteur: false,
      }
  },
  methods: {
    go() {
      this.chrono = true
      this.minuteur = false
    },

    minu() {
      this.chrono = false
      this.minuteur = true
    }
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

body {
  background-color: rgb(132, 132, 255);
}

#sidebarApp {
  position: absolute;
  left: 0;
  top: 0;
  height: 100vh;
  width: 120px;
  background-color: rgb(209, 209, 209);
  border: transparent 2px solid;
  box-shadow: rgb(90, 90, 90) 4px 0px 5px;
}

#application {
  width: 90%;
  margin-left: 7%;
  padding-bottom: 100px;
  height: 80vh;
  border: grey 2px solid;
  background-color: rgb(209, 209, 209);
  border-radius: 25px;
}
</style>
