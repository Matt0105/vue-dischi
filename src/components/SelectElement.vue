<template>
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
</template>

<script>
export default {
    name: "SelectElement",
}
</script>

<style lang="scss" scoped>

</style>