<template>

  <div class="card">
      <div class="thumb">
          <img :src="image" alt="">
          <i class="fas fa-play play-btn"></i>
      </div>
      <div class="card-info">
          <h2>{{ title }}</h2>
          <h3>{{ author }}</h3>
          <h4>{{ year }}</h4>
      </div>
  </div>

</template>

<script>
export default {
    name: "CardElement",
    props: {
        image: {
            type: String,
            default: null
        },
        title: {
            type: String,
            required: true,
        },
        author: {
            type: String,
            required: true,
        },
        year: {
            type: String,
            default: null
        }
    }
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/partials/_variables.scss";

    .card {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: calc(100% / 5 - 3rem);
        padding-top: 1.2rem;
        border-radius: 10px;
        background-color: $light-blue;

        .thumb {
            position: relative;
            width: 100%;
            text-align: center;
            cursor: pointer;


            &:hover img {
                filter: brightness(50%);
                transform: scale(1.1);
            }
            img {
                width: 70%;

                transition: all .3s;
            }

            &:hover .play-btn {
                display: block;
            }
            .play-btn {
                display: none;
                position: absolute;
                top: 50%;
                left: 50%;
                transform: translate(-50%, -50%);
                font-size: 2rem;
                color: white;

                
            }
        }

        .card-info {
            color: white;
            margin: 0.8rem;
            padding-bottom: 1rem;
            text-align: center;

            h2 {
                text-transform: uppercase;
                font-size: 1.2rem;
                margin-bottom: 1rem;
            }

            h3, h4 {
                color: gray;
                font-weight: 500;
            }

            h3 {
                font-size: 1rem;
            }

            h4 {
                font-size: 0.9rem;
            }
        }
    }


</style>