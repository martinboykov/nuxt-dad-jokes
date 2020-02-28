<template>
  <div>
    <nuxt-link to="/jokes" class="link">Back to Jokes</nuxt-link>
    <h2>{{joke}}</h2>
    <hr />
    <small>Joke ID: {{$route.params.id}}</small>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      joke: ""
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json"
      }
    };
    try {
      const res = await axios.get(
        `https://icanhazdadjoke.com/j/${this.$route.params.id}`,
        config
      );
      this.joke = res.data.joke;
    } catch (error) {
      console.log(error);
    }
  }
};
</script>

<style>
.link{
  display: inline-block;
  background: #333;
  color: #fff;
  padding: 0.3rem 1rem;
  margin-right: 0.5rem;
}
</style>
