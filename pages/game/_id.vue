<template>
    <div>
      <div v-if="loading" class="text-center">Loading...</div>
      <div v-else>
        <h1 class="text-3xl font-bold mb-5">{{ game.title }}</h1>
        <p>{{ game.platform }}</p>
        <p>{{ game.short_description }}</p>
        <img :src="game.thumbnail" alt="">
        <div class="mt-2">
          <nuxt-link to="/" class="text-blue-600 hover:text-blue-800">Back to List</nuxt-link>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    async asyncData({ $axios, params }) {
      const response = await $axios.get(`https://www.mmobomb.com/api1/game?id=${params.id}`)
      return {
        game: response.data,
        loading: false
      }
    },
  }
  </script>