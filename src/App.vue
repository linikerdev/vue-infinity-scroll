<template>
  <div id="app">
    <ul
      v-infinite-scroll="loadMore"
      infinite-scroll-disabled="busy"
      infinite-scroll-distance="100"
    >
      <li v-for="x in list" :key="x">numero: {{ x }}</li>
      <img v-if="loading" :src="img" alt="" />
    </ul>
  </div>
</template>

<script>
import imgLoad from "@/assets/spinner.gif";
export default {
  name: "App",
  data() {
    return {
      loading: false,
      img: imgLoad,
      list: 100
    };
  },
  methods: {
    loadMore: function() {
      this.loading = true;

      setTimeout(() => {
        this.loading = false;
        this.list += 100;
      }, 3000);
    }
  }
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
li {
  width: 80%;
  background-color: #ccc;
  margin: 4px;
  padding: 5px;
}
</style>
