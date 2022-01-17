<template>
  <main>
    <div class="container">
      <CardElement />
    </div>
  </main>
</template>

<script>
import CardElement from './CardElement.vue'
export default {
  components: { CardElement },
    name: "Main",
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
    width: 80%;
    height: 100%;
    margin: 0 auto;
    padding-top: 3rem;
  }

</style>