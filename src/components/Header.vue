<template>
  <header>
      <nav>
          <img src="../assets/img/17-176153_download-logo-spotify-png.png" alt="">
      </nav>
  </header>
</template>

<script>
export default {
    name: "Header",
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/partials/_variables.scss";

    nav {
        display: flex;
        align-items: center;
        width: 100%;
        height: 60px;
        background-color: $light-blue;

        img {
            height: 85%;
            margin-left: 5px;
        }
    }

    
</style>