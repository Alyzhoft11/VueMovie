<template>
  <div class="-mt-3 ml-1 absolute z-20">
    <button @click="back" class="p-3 w-12 h-12 text-white bg-gray-800 hover:bg-gray-900 rounded-full active:shadow-lg mouse shadow">
      <svg class="w-6 h-6 fill-current" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
        <path fill-rule="evenodd" d="M7.707 14.707a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414l4-4a1 1 0 011.414 1.414L5.414 9H17a1 1 0 110 2H5.414l2.293 2.293a1 1 0 010 1.414z" clip-rule="evenodd"></path>
      </svg>
    </button>
  </div>
  <div class="flex m-4 relative">
    <img :src="movie.Poster" :alt="movie.Title" />
    <div>
      <h1 class="ml-4 text-xl font-bold"><span class="text-2xl font-bold">Title: </span>{{ movie.Title }}</h1>
      <h1 class="ml-4 text-xl font-bold"><span class="text-2xl font-bold">Year: </span>{{ movie.Year }}</h1>
      <h1 class="ml-4 text-xl font-bold"><span class="text-2xl font-bold">Rated: </span>{{ movie.Rated }}</h1>
      <h1 class="ml-4 text-xl font-bold"><span class="text-2xl font-bold">Released: </span>{{ movie.Released }}</h1>
      <h1 class="ml-4 text-xl font-bold"><span class="text-2xl font-bold">Runtime: </span>{{ movie.Runtime }}</h1>
      <h1 class="ml-4 text-xl font-bold"><span class="text-2xl font-bold">Genre: </span>{{ movie.Genre }}</h1>
      <h1 class="ml-4 text-xl font-bold"><span class="text-2xl font-bold">Director: </span>{{ movie.Director }}</h1>
      <h1 class="ml-4 text-xl font-bold"><span class="text-2xl font-bold">Writer: </span>{{ movie.Writer }}</h1>
      <h1 class="ml-4 text-xl font-bold"><span class="text-2xl font-bold">Actors: </span>{{ movie.Actors }}</h1>
    </div>
  </div>
  <p class="ml-4 mt-4 mr-6">{{ movie.Plot }}</p>
  <div class="flex justify-center mt-12">
    <div
      v-for="rating in movie.Ratings"
      :key="rating.Source"
      class="mr-2 py-2 px-4 shadow-md no-underline rounded-full text-white bg-gray-800 font-sans font-semibold text-sm border-red btn-primary hover:text-white hover:bg-red-light focus:outline-none active:shadow-none"
    >
      <span>{{ rating.Source }}:</span> {{ rating.Value }}
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: 'MovieDetails',
  props: { movie: Object },
  emits: ['back'],
  setup(props: any, { emit }: any) {
    const back = () => {
      emit('back');
    };

    return {
      back,
    };
  },
};
</script>
