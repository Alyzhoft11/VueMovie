<template>
  <div @click="posterClicked(movie.imdbID)" class="rounded-md border-black border-2 shadow-md h-xl sm:w-full md:w-full lg:w-1/6 xl:w-1/6">
    <img class="w-full h-auto" :src="movie.Poster" alt="Sunset in the mountains" />
    <div class="px-6 py-4">
      <div class="font-bold text-lg my-4">{{ movie.Title }}</div>
    </div>
  </div>
</template>

<script lang="ts">
import { ref, reactive } from 'vue';

export default {
  name: 'Card',
  props: { movie: Object },
  emits: ['movie-data'],
  setup(props: any, { emit }: any) {
    const posterClicked = async (id: string) => {
      const url = `http://omdbapi.com/?i=${id}&plot=full&apikey=6fba8f72`;

      const response = await fetch(url);

      const movieData = await response.json();

      emit('movie-data', movieData);
    };

    return {
      posterClicked,
    };
  },
};
</script>
