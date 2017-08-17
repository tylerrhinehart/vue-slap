<template>
  <div class="hello">
    <h1 :class="{red: target.health <= 25, green: target.health > 75, orange: target.health <=75 && target.health > 25}">{{ target.name }} {{ target.health }}</h1>
    <button class="btn btn-primary" v-if="target.health > 0" @click="slap">Slap {{ target.name }}</button>
    <button class="btn btn-danger" :disabled="target.health <= 0" @click="curbStomp">Curb-stomp {{ target.name }}</button>
    <button class="btn btn-success" @click="reset">Reset</button>
    <div>
        <img :src="target.img">
    </div>
  </div>
</template>

<script>
export default {
  name: 'hello',
  props: ['target'],
  data() {
    return {
    }
  },
  methods: {
    slap() {
      this.target.health -= 1
      this.checkHealth()
    },
    curbStomp() {
      this.target.health -= 5
      this.checkHealth()
    },
    checkHealth() {
      if (this.target.health < 0) {
        this.target.health = 0
      }
    },
    reset() {
      this.target.health = 100
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.red {
  color: red;
}

.green {
  color: green;
}

.orange {
  color: orange;
}
img{
  height: 200px;
  width: 200px;
}
</style>
