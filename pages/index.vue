<template>
  <div>
    <h1 class="text-3xl font-bold mb-5">List Games</h1>
    <div v-if="loading" class="text-center">Loading...</div>
    <div v-else>
      <ul>
        <li v-for="game in games" :key="game.id">
          <nuxt-link :to="`/game/${game.id}`">{{ game.title }}</nuxt-link>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
  export default {
    async asyncData({ $axios }) {
      const response = await $axios.get('https://www.mmobomb.com/api1/games?platform=pc')
      return {
        games: response.data,
        loading: false
      }
    },
  }
</script>
