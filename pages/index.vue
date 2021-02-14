<template>
  <div class="container">
    <div class="search-bar">
      <input type="text" name="search" id="search" class="search-text-box no-border" v-model="search_parameter" placeholder="Search for Movies...">
      <input type="button" value="SEARCH" class="search-button no-border" @click="getMovies()">
    </div>
    <div class="movie-cards-container" >
      <movie-card
        v-bind:key="movie.id"
        v-for="movie in movies"
        :movie="movie"></movie-card>
    </div>
  </div>
</template>

<script lang="ts">
// import Vue from 'vue'
import movie_card from '~/components/movie_card.vue'

export default {
  data () {
    return {
      search_parameter: '',
      movies: {}
    }
  },
  components: { movie_card },
  methods: {
    getMovies() {
      const searchParams = new URLSearchParams();
      searchParams.append('search', this.search_parameter)
      this.$axios.$get(`/movies?${searchParams}`)
      .then((response:any) => {
        console.log(response)
        this.movies = response;
      })
    }
  },
  beforeMount () {

  }
  }
</script>

<style>
body {
  background-color: #85DCBE;
}

.container {
  margin: 0;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

input:focus {
  outline: none;
}

.search-bar {
  width: 100%;
  background-color: #41B3A3;
  display: flex;
  flex-direction: row;
  height: 100px;
  padding: 20px;
  justify-content: center;
}

::placeholder {
  color: #FFA;
}

.no-border {
  border: none;
}

.search-text-box {
  color: white;
  font-size: 20px;
  font-weight: 900;
  letter-spacing: 3px;
  width: 50%;
  line-height: 10px;
  background-color: #41B3A3;
  border-bottom: 4px solid #85DCBE;
}

.search-button {
  color: white;
  font-size: 20px;
  letter-spacing: 3px;
  background-color: #E27D60;
  width: 20%;
  border-bottom: 4px solid #E27D60;
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
  border-bottom-right-radius: 5px;

}

.movie-cards-container {
  width: 100%;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
