<template>
  <div class="card">
      <div class="thumb">
          <img src="https://picsum.photos/200" alt="">
      </div>
      <div class="card-info">
          <h2>Title</h2>
          <h3>Artist</h3>
          <h4>Year</h4>
      </div>
  </div>
</template>

<script>
export default {
    name: "CardElement",
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/partials/_variables.scss";

    .card {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: calc(100% / 5);
        height: calc(100% / 2);
        padding-top: 2rem;
        background-color: $light-blue;

        .thumb {
            width: 100%;
            text-align: center;

            img {
                width: 70%;
            }
        }

        .card-info {
            color: white;
            margin-top: 1rem;
            text-align: center;

            h2 {
                text-transform: uppercase;
                font-size: 2rem;
                margin-bottom: 1.5rem;
            }

            h3, h4 {
                color: gray;
                font-weight: 500;
            }

            h3 {
                font-size: 1.5rem;
            }

            h4 {
                font-size: 1.2rem;
            }
        }
    }


</style>