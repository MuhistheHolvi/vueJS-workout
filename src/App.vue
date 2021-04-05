<template>
  <div id="app" @hover="hideButtons">
    <h2>Planets concoured</h2>
    <ul>
      <li
        v-for="world in concqueredWorlds"
        :key="world"
        @mouseover="deleteButtonWorld = world"
        @mouseleave="deleteButtonWorld = null"
      >
        {{ world }} :
        <button @click="removeWorld(world)" v-show="showButton(world)">
          Retreat from world
        </button>
      </li>
    </ul>
    <h2>Free planets</h2>
    <ul>
      <li
        v-for="world in freeWorlds"
        :key="world"
        @mouseover="deleteButtonWorld = world"
        @mouseleave="deleteButtonWorld = null"
      >
        {{ world }}
        <button @click="invadeWorld(world)" v-show="showButton(world)">
          Invade world
        </button>
      </li>
    </ul>
    <h2>Planetary logs</h2>
    <ul>
      <li v-for="log in planetaryLogs" :key="log">{{ log }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      concqueredWorlds: ["Earth"],
      freeWorlds: [
        "Saturn",
        "Uranus",
        "Neptune",
        "Moon",
        "Mercury",
        "Mars",
        "Jupitor",
        "Venus",
      ],
      deleteButtonWorld: null,
      planetaryLogs: [],
    };
  },
  methods: {
    log(message) {
      this.planetaryLogs.push(message);
    },
    removeWorld(world) {
      if (this.freeWorlds.includes(world)) {
        this.log(`Trying to remove ${world} failed, free world.`);
      } else {
        this.hideButtons();
        this.concqueredWorlds = this.concqueredWorlds.filter(
          (item) => item != world
        );
        this.freeWorlds.push(world);
        this.log(`Removed the world ${world}.`);
      }
    },
    showButton(world) {
      return this.deleteButtonWorld == world;
    },
    hideButtons() {
      this.deleteButtonWorld = null;
    },
    invadeWorld(world) {
      if (this.freeWorlds.includes(world)) {
        this.hideButtons();
        this.concqueredWorlds.push(world);
        this.freeWorlds = this.freeWorlds.filter((item) => item != world);
        this.log(`The world ${world} was invaded.`);
      } else {
        this.log(`Failed in invading ${world}, the world is already invaded.`);
      }
    },
  },
};
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
button {
  background-color: #f44336;
}
</style>
