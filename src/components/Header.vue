<template>
  <header>
      <nav>
          <img src="../assets/img/17-176153_download-logo-spotify-png.png" alt="">
          <div class="search-container">
            <input class="search" type="text">
            <button>Search</button>
          </div> 

          
      </nav>
  </header>
</template>

<script>

export default {
    name: "Header",
    data() {
        return {
        }
    },
    mounted() {
    },

    methods: {
       
    }
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

        .search-container {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 100%;
            height: 100%;
            margin: auto;

            .search {
                width: 25%;
                height: 40%;
                background-color: rgb(170, 167, 167);
                border: none;
                border-radius: 5px;
                outline-color: #18D860;
            }

            button {
                background-color: #18D860;
                border: none;
                padding: 8px;
                text-transform: uppercase;
                border-radius: 5px;
                margin-left: 10px;

                cursor: pointer;
            }
        }
        
    }

    
</style>