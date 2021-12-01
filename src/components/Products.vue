<template>
<h1>מוצרים</h1>
<div class="conteiner">

<div v-if="filterProductList.length!==0" >
    <div v-for="(prod, i) in filterProductList" :key="i">
        <Product :product="prod"/>
    </div>
</div>
<div v-else>
  <div v-for="(prod, i) in productList" :key="i">
        <Product :product="prod"/>
    </div>
</div>
</div>
</template>

<script>
import Product from './Product'

export default {
    name:'Products',
    props:{
        filterProductList: Array,
        productList:Array,
    },
    components:{
        Product
    }
}
</script>

<style scoped>
.conteiner{
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;  
  float: right;
  justify-content: center;
}

</style>
