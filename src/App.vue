<template>
  <div id="app">
    <button v-on:click="toast">Start toasting</button>
    <ul v-show="showCountDown">
      <p>Toasting</p>
      <li v-for="number in countDown" :key="number">{{ number }}</li>
    </ul>
    <p v-show="toastingDone">Toasting done, enjoy your toast</p>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      countDown: 0,
      toastingDone: false,
      showCountDown: false,
    };
  },
  methods: {
    toast() {
      setInterval(() => {
        const isToast = isBreadToast(this.countDown);
        if (isToast) {
          this.toastingDone = true;
        } else {
          this.countDown++;
          this.showCountDown = true;
        }
      }, 1000);
    },
  },
};
function isBreadToast(counter) {
  if (counter == 10) {
    return true;
  } else {
    counter++;
    return false;
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
