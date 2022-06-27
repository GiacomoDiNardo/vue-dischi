<template>
  <div id="app">
  <TheHeader :genre-list="genreList" @changeGenre="onChangeGenre($event)" />
  <CardContainer @genresList="onGenresUpdate" :changeGenre="changeGenre" />
  </div>
</template>

<script>
import TheHeader from "./components/TheHeader.vue"
import CardContainer from "./components/CardContainer.vue"



export default {
  name: 'App',
  components: {
    TheHeader,
    CardContainer,
  },

  data() {
    return {
      genreList: [],
      changeGenre: "",
    }
  },

  methods: {
    onGenresUpdate(genreList) {
      this.genreList = genreList;
    },

    onChangeGenre(genre) {
      this.changeGenre = genre;
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
