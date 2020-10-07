<template>
  <div class="flex items-center justify-end bg-gray-800 p-4">
    <form @submit.prevent="getData">
      <div class="ml-3">
        <input v-model="searchValue" placeholder="Search" type="text" name="search" id="search" class="flex shadow appearance-none border border-black rounded-md w-64 px-3 text-gray-700 focus:outline-none focus:shadow-outline" />
      </div>
    </form>
  </div>
</template>

<script lang="ts">
import { ref, reactive } from 'vue';

export default {
  name: 'Search',
  emits: ['data'],
  setup(props: any, { emit }: any) {
    const searchValue = ref(null);
    const movies = reactive({
      searchs: [],
    });

    const getData = async () => {
      const url = `http://www.omdbapi.com/?s=${searchValue.value}&apikey=6fba8f72`;

      const response = await fetch(url);

      const moviesData = await response.json();

      //   console.log(movieData);

      movies.searchs = moviesData.Search;

      emit('data', movies.searchs);
    };

    return {
      searchValue,
      getData,
      movies,
    };
  },
};
</script>
