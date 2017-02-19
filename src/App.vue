<template>
  <div id="app">
    <search v-on:SearchRequested="handleSearch"></search>
    <preview v-bind:gifs=gifs></preview>
    <p v-if="isloading">Loading...</p>
  </div>
</template>


<script>
import Search from './components/Search.vue'
import Preview from './components/Preview.vue'
export default {
  name: 'app',
  components: { Search, Preview },
  data() {
    return{
      isloading: true,
      gifs: []
    }
  },
  methods: {
    doQuery(url) {
      fetch(url)
      .then((res) => { return res.json() })
      .then((res) => {
        this.gifs = res.data;
        this.isloading = false;
      })
    },
    handleSearch(query) {
      console.log(query);
      this.gifs = [];
      this.isloading = true;
      const url = `http://api.giphy.com/v1/gifs/search?q=${query}&api_key=dc6zaTOxFJmzC`;
      this.doQuery(url);
    }
  },
  created() {
    const url = `http://api.giphy.com/v1/gifs/trending?api_key=dc6zaTOxFJmzC`;
    this.doQuery(url);
  }
}
</script>


<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 50px;
}
</style>

