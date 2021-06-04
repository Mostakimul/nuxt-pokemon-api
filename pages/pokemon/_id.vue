<template>
  <div class="container">
    <div
      class="
        py-1.5
        bg-green-500
        text-white text-lg
        uppercase
        rounded-xl
        shadow-lg
      "
    >
      <h2 class="">{{ $route.params.id }}</h2>
    </div>

    <div
      class="
        flex
        justify-between
        bg-green-500
        text-white
        mt-2
        shadow-lg
        p-2
        rounded-xl
      "
    >
      <div class="grid place-items-center">
        <p>Base Experience: {{ details.base_experience }}</p>
        <p>Height: {{ details.height }}</p>
        <p>Height: {{ details.weight }}</p>
        <div v-for="(type, index) in details.types" :key="index">
          <h5>Type: {{ type.type.name }}</h5>
        </div>
      </div>

      <div class="justify-center bg-red-700 py-2 rounded-xl">
        <div class="flex">
          <img
            :src="((details || {}).sprites || {}).back_default"
            alt="Back Default"
            class="bg-gray-50 m-1 rounded-xl"
          />
          <img
            :src="((details || {}).sprites || {}).back_shiny"
            alt="Back Default"
            class="bg-gray-50 m-1 rounded-xl"
          />
        </div>
        <div class="flex">
          <img
            :src="((details || {}).sprites || {}).front_default"
            alt="Back Default"
            class="bg-gray-50 m-1 rounded-xl"
          />
          <img
            :src="((details || {}).sprites || {}).front_shiny"
            alt="Back Default"
            class="bg-gray-50 m-1 rounded-xl"
          />
        </div>
      </div>
    </div>

    <!-- <div>
      <h5>Species:{{ ((details || {}).species || {}).name }}</h5>
    </div> -->
  </div>
</template>

<script>
// import axios from 'axios'
export default {
  data() {
    return {
      details: {},
    }
  },

  mounted() {
    fetch('https://pokeapi.co/api/v2/pokemon/' + this.$route.params.id)
      .then((res) => res.json())
      .then((data) => {
        this.details = data
        // console.log(data)
      })
  },
  // async asyncData({ params, $http }) {
  //   const post = await axios
  //     .get(`https://pokeapi.co/api/v2/pokemon/${params.id}`)
  //     .then((res) => res.json())
  //   console.log(post)
  //   return { post }
  // },
}
</script>

<style scoped>
.container {
  max-width: 600px;
  margin: 0 auto;
  min-height: 100vh;
  text-align: center;
}
</style>
