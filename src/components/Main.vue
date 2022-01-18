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
    <div v-else>
      LOADING
    </div>

    <div class="select-filter">
      <select @change="selectGenre()" v-model="genre" name="genre" id="genre">

        <option value="all">All</option>

        <option 
          v-for="(genre, index) in genreList" 
          :key=index
          :value="genre">{{genre}}
        </option>
      </select>
    </div> 

    <div class="select-filter">
      <select @change="selectArtist()" v-model="artist" name="artist" id="artist">

        <option value="all">All</option>

        <option 
          v-for="(artist, index) in artistList" 
          :key=index
          :value="artist">{{artist}}
        </option>
      </select>
    </div> 
  </main>
</template>

<script>

import CardElement from './CardElement.vue';
import axios from 'axios';

export default {
  components: { 
    CardElement 
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

    this.getData();

  },
  methods: {

    getData() {

      axios.get(this.apiQuery)
      .then((response) => {
        this.musicData = response.data.response;
        this.myData = this.musicData;
        this.getGenre();
        this.getArtist();

        // console.log(this.musicData);
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

      // console.log(this.artistList);

    },

    selectGenre() {

      if(this.genre == "all") {
        this.myData = this.musicData;
      }
      else {
        this.artist = "all";
        this.myData = this.musicData.filter((el) => {
          return el.genre === this.genre;
        });
      }

      // console.log(this.myData);
    },

    selectArtist() {

      console.log(this.artist);
      if(this.artist == "all") {
        this.myData = this.musicData;
      }
      else {
        this.genre = "all";
        this.myData = this.musicData.filter((el) => {
          return el.author === this.artist;
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
    // height: calc(100vh - 60px);
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