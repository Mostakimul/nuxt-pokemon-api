<template>
  <div class="container">
    <table class="table-auto bg-green-600 p-3 rounded shadow-lg text-white">
      <thead>
        <tr>
          <th>Pokemon Name</th>
          <th>Pokemon Details</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="pokemon in pokemons" :key="pokemon.name">
          <td>{{ pokemon.name }}</td>
          <td>
            <NuxtLink
              :to="`/pokemon/${pokemon.name}`"
              class="bg-green-900 rounded-lg p-2"
              >Details</NuxtLink
            >
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pokemons: [],
    }
  },
  mounted() {
    fetch('https://pokeapi.co/api/v2/pokemon')
      .then((response) => response.json())
      .then((data) => {
        this.pokemons = data.results
        // console.log(data)
      })
  },
}
</script>

<style scoped>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

/* .links {
  padding-top: 15px;
} */
</style>
