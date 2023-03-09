<template>
    <div>
      <form @submit.prevent="addGame">
        <div class="mb-4">
          <label for="title" class="block text-gray-700 font-bold mb-2">Title:</label>
          <input type="text" id="title" v-model="game.title" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline">
        </div>
        <div class="mb-4">
          <label for="platform" class="block text-gray-700 font-bold mb-2">Platform:</label>
          <input type="text" id="platform" v-model="game.platform" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline">
        </div>
        <div class="mb-4">
          <label for="description" class="block text-gray-700 font-bold mb-2">Description:</label>
          <textarea id="description" v-model="game.description" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"></textarea>
        </div>
        <div class="mb-4">
          <button type="submit" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">Add Game</button>
        </div>
      </form>
    </div>
</template>
  
<script>
    export default {
        data() {
        return {
            game: {
            title: '',
            platform: '',
            description: ''
            }
        }
        },
        methods: {
        addGame() {
            // Lakukan proses POST data game menggunakan API dummy
            fetch('https://dummyapi.com/games', {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify(this.game)
            })
            .then(response => {
            if (!response.ok) {
                throw new Error('Failed to add game')
            }
            // Kembali ke halaman List Page
            this.$router.push('/')
            })
            .catch(error => {
            console.log(error)
            })
        }
        }
    }
  </script>