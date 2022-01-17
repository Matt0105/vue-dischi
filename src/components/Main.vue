<template>
  <main>
    <div v-if="musicData" class="container">
      <CardElement 
        v-for="(element, index) in musicData"
        :key=index
        :image=element.poster
        :title=element.title
        :author=element.author
        :year=element.year
      />
    </div>
    <div v-else>
      LOADING
    </div>
  </main>
</template>

<script>

import axios from 'axios';
import CardElement from './CardElement.vue';

export default {
  components: { 
    CardElement 
  },
  name: "Main",
  data() {
    return {
      apiQuery: "https://flynn.boolean.careers/exercises/api/array/music",
      musicData: null,
    }
  },
  mounted() {

    this.getData();

  },
  methods: {

    getData() {

      axios.get(this.apiQuery)
      .then((response) => {
        this.musicData = response.data.response;
        console.log(this.musicData);
      })
      .catch((err) => {
        console.log(err);
      });
    }

  }
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/partials/_variables.scss";

  main {
    width: 100%;
    height: calc(100vh - 60px);
    background-color: $dark-blue;
  }

  .container {
    display: flex;
    flex-wrap: wrap;
    gap: 2rem 3rem;
    width: 80%;
    height: 100%;
    margin: 0 auto;
    padding: 2rem 0;
  }

</style>