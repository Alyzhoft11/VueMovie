<template>
  <div>
    <Search @data="setMovies" />
    <div v-if="Object.keys(movie).length === 0" class="flex flex-wrap justify-center mt-6">
      <Card @movie-data="setMovie" class="mx-2 mb-2" v-for="m in movies" :key="m.imdbID" :movie="m" />
    </div>
    <div v-else-if="Object.keys(movie).length > 0">
      <MovieDetails @back="back" :movie="movie" />
    </div>
  </div>
</template>

<script lang="ts">
import { ref } from 'vue';
import Search from './components/Search.vue';
import Card from './components/Card.vue';
import MovieDetails from './components/MovieDetails.vue';

export default {
  components: {
    Search,
    Card,
    MovieDetails,
  },

  setup() {
    const movies = ref([]);
    const movie = ref({});

    const setMovies = (v: any) => {
      movie.value = {};
      movies.value = v;
    };

    const setMovie = (v: any) => {
      movie.value = v;
    };

    const back = () => {
      movie.value = {};
    };

    // const ratingColor = (rating: any) => {
    //   let temp: number = 0;
    //   let val: string

    //   switch (rating.Source) {
    //     case 'Internet Movie Database':
    //       temp = parseInt(rating.split('/')[0]) * 100;
    //       break;

    //     case 'Rotten Tomatoes'
    //       temp = parseInt(rating.replace('%', ''));
    //       break

    //     case 'Metacritic'
    //       temp = parseInt(rating.split('/')[0])
    //       break
    //   }

    //   if (temp >= 85) {
    //    val = 'bg-green-500';
    //   } else if (temp < 85 && temp >= 70) {
    //     val = 'bg-yellow-500';
    //   } else {
    //     val = 'bg-red-500';
    //   }

    //   return val;
    // };

    return {
      setMovies,
      movies,
      setMovie,
      movie,
      back,
      // ratingColor,
    };
  },
};
</script>
