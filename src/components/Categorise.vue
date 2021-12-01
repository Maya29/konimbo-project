<template>
    <h1>{{title}}</h1>
    <div class="categoryList" v-for="(cat, i) in categorisTitle" :key="i">
        <p @click="chosenCat(cat)">{{cat}}</p>
    </div>
</template>

<script>
export default {
    name:'Categorise',
    props:{
        title: String,
        categorisTitle: Array,
    },
    methods:{
       chosenCat(val){
           this.$emit('chosen-category',val)
       } 
    }
}
</script>

<style scoped>

</style>
