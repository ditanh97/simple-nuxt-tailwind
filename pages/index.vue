<template>

  <div class="bg-white p-6">
    <h1 class="text-3xl font-bold mb-5">List Games</h1>
    <div v-if="loading" class="text-center">Loading...</div>
    <div v-else>
      <div class="mt-4">
        <nuxt-link to="/add-game" class="text-blue-600 hover:text-blue-800">Add Game</nuxt-link>
      </div>
      <div v-if="games.length > 0">
        <div v-for="game in games" :key="game.id" class="mb-4">
          <h2 class="text-lg font-bold mb-2">{{ game.title }}</h2>
          <p class="text-gray-700">{{ game.platform }}</p>
          <div class="mt-2">
            <nuxt-link :to="'/game/' + game.id" class="text-blue-600 hover:text-blue-800">Details</nuxt-link>
          </div>
        </div>
      </div>
      <div v-else>
        <p>No games found.</p>
      </div>
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
