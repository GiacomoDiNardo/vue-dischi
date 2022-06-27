<template>
  <div class="container py-4">

    <select class="form-select" aria-label="Default select example" v-model="genre" @change="changeGenre()">
      <option selected>Filtra per genere</option>
      <option v-for="(genre, i) in genreList" :key="i" :value="genre">{{ genre }}</option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    genreList: Array,
  },
  data() {
    return {
      genre: "",
    }
  },

  methods: {
    changeGenre() {
      this.$emit("changeGenre", this.genre);
    }
  }
};
</script>
