<template>
  <div id="app">
      <ul>
        <li v-for="(sound, animal) in animals" :key="animal"> Animal {{animal}} says hello world as: {{sound}}.</li>
      </ul>    
  </div>
</template>

<script>
  export default {
    name: 'App',
    data() {
      return {
        animals: {
          dog: "HowHow",
          cat: "MeowMeow",
          cow: "MooMoo",
        }
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
  margin-top: 60px;
}
#div {
  height: 200px;
  width: 50%;
}
</style>
