<template>
    <div>
      <h1 class="text-3xl font-bold mb-5">{{ game.title }}</h1>
      <div v-if="loading" class="text-center">Loading...</div>
      <div v-else>
        <p>{{ game.short_description }}</p>
        <img :src="game.thumbnail" alt="">
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