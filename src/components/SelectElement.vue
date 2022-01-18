<template>
  <div class="select-filter">
    <select @change="passSelection()" v-model="selection" name="sel" id="sel">

        <option value="all">All</option>

        <option 
            v-for="(element, index) in myList" 
            :key=index
            :value="element">{{element}}
        </option>
    </select>
    </div> 
</template>

<script>
export default {
    name: "SelectElement",

    props: {
        myList: [],
        option: String,
        reset: Boolean
        
    },

    data () {
        return {
            selection: "all"
        }
    },

    methods: {
        passSelection() {
            
            this.$emit('choice', this.selection);
        }
    }
}
</script>

<style lang="scss" scoped>

    .select-filter {
        display: inline-block;

        select {
            border: none;
            padding: 1rem;
            border-radius: 20px;
            background-color: rgb(170, 167, 167);
            border: 3px solid #18D860;
            outline: none;
            margin: 15px;
        }
    }
    
</style>