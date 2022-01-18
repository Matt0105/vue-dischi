<template>
  <main>
    <div v-if="musicData" class="container">
      <CardElement 
        v-for="(element, index) in myData"
        :key=index
        :image=element.poster
        :title=element.title
        :author=element.author
        :year=element.year
      />
    </div>
    <div class="loading" v-else>
      <span><i class="fas fa-spinner loading-spinner"></i></span>
    </div>

    <div v-if="myData" class="select-container">

      <div class="genre-select">
        <h3>Genre:</h3>
        <SelectElement
          :myList="genreList"
          @choice="selectGenre($event), genre = $event"
        />
      </div>

      <div class="artist-select">
        <h3>Artist:</h3>
        <SelectElement
          :myList="artistList"
          @choice="selectArtist($event), artist = $event"
        />
      </div>
    </div>
    

  </main>
</template>

<script>

import CardElement from './CardElement.vue';
import SelectElement from './SelectElement.vue';
import axios from 'axios';

export default {
  components: { 
    CardElement,
    SelectElement
  },
  name: "Main",
  data() {
    return {
      apiQuery: "https://flynn.boolean.careers/exercises/api/array/music",
      musicData: null,
      myData: null,
      genre: "all",
      artist: "all",
      genreList: [],
      artistList: [],

    }
  },
  mounted() {

    setTimeout(() => {
      this.getData();
    }, 2000);
    
  },
  methods: {

    getData() {

      axios.get(this.apiQuery)
      .then((response) => {
        this.musicData = response.data.response;
        this.myData = this.musicData;
        this.getGenre();
        this.getArtist();

      })
      .catch((err) => {
        console.log(err);
      });
    },

    getGenre() {
    
      this.musicData.forEach(element => {
        if(!this.genreList.includes(element.genre)) {
            this.genreList.push(element.genre);
        }
      });

    },
    
    getArtist() {

      this.musicData.forEach(element => {
        if(!this.artistList.includes(element.author)) {
            this.artistList.push(element.author);
        }
      });

    },

    selectGenre(selection) {

      if(selection == "all") {
        this.myData = this.musicData;
      }
      else {
        this.artist = "all";
        this.myData = this.musicData.filter((el) => {
          return el.genre === selection;
        });
      }

    },

    selectArtist(selection) {

      if(selection == "all") {
        this.myData = this.musicData;
      }
      else {
        this.genre = "all";
        this.myData = this.musicData.filter((el) => {
          return el.author === selection;
        });
      }
    }

  }
}
</script>

<style lang="scss" scoped>
@import "../assets/scss/partials/_variables.scss";

  main {
    width: 100%;
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

  .loading {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);

    span {
      color: white;
      text-transform: uppercase;
      font-size: 2rem;
      font-weight: 600;

      .loading-spinner {
        animation: spin-animation 2s infinite;
      }
    }
  }

  .select-container {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    text-align: center;

      .genre-select, .artist-select {
        display: inline-block;

        h3 {
          color: white;
          text-transform: uppercase;
          font-size: 0.8rem;
        }
      }
  }


  @keyframes spin-animation {
    0% {
    transform: rotate(0deg);
    }
    100% {
      transform: rotate(359deg);
    }
  }

</style>