<template>
  <div id="app">
    <button @click="resetAll">Reset All</button>
    <div v-for="opponent in opponents">
      <slap :target="opponent"></slap>
    </div>
  </div>
</template>

<script>
  import Slap from './components/Slap'

  export default {
    name: 'app',
    data() {
      return {
        opponents: [
          { name: 'Mark', health: 100, img: '//media.licdn.com/mpr/mpr/shrinknp_200_200/AAEAAQAAAAAAAAKPAAAAJDIyNmZlYWIxLTUwZjYtNDg2My04N2Q3LTJiODBhMzIwYWVhOA.jpg' },
          { name: 'Treebeard', health: 100, img: '//upload.wikimedia.org/wikipedia/en/2/2e/Treebeard.jpg' }
        ]

      }
    },
    methods: {
      resetAll() {
        for (var i = 0; i < this.opponents.length; i++) {
          var opponent = this.opponents[i]
          opponent.health = 100
        }
      }
    },
    components: {
      Slap
    }
  }

</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>