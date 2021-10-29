<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div v-for="item in items" :key="item">
    <Child v-bind:message="item.message" v-bind:name="item.name"></Child>
  </div>
</template>

<script lang="ts">
import {Options, Vue} from 'vue-class-component';
import Child from "@/Child.vue";
@Options({
  components: {
    Child
  },
  data() {
    return {
      items: [],
    }
  },
  methods:
      {
        load: function () {
          console.log("load start")
          fetch('./data.json')
              .then(response => {
                return response.json();
              })
              .then(json => {
                this.items = json.data;
                setTimeout(() =>
                {
                  console.log("reload start")
                  this.load();
                } , 1000)
              })
        }
      },
  mounted() {
    this.load();
  }
})
export default class App extends Vue {
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
</style>