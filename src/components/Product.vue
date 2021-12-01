<template>
<div class="conteiner">
  <div class="box">
    {{ product.title }} <br/>
    <img id="Image" :src="product.images[0] ? product.images[0].url : NoImageText" alt=""/>
     {{ product.price }}<br/>
    {{ product.desc }}<br/>
     <router-link :to="{ name: 'About',  params: { data: JSON.stringify(product) } }">למוצר</router-link>
  </div>
</div>
</template>

<script>
export default {
  name: "Product",
  props: {
    product: Object,
  },
 data(){
     return{
         NoImageText:"No Image"
     }
 }
};
</script>

<style scoped>
.conteiner{
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
    float: right;
}
.box{
    display: flex;
      flex: 1;
    flex-direction: column;
   width:20rem;
    height:22rem;
  margin: 30px auto;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
  align-items: center;
}
#Image {
   border-radius: 8px;
    width:10rem;
    height:10rem;
}
</style>
