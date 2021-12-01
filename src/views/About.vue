<template>
  <div class="about">
    <div class="rowItems">
      <h3 id="back"><router-link to="/">חזרה</router-link></h3>
    <h2>{{ product.title }}</h2>
    </div>
    <div class="allImag" v-for="(prod, i) in product.images" :key="i">
      <img id="Image" :src="prod ? prod.url : NoImageText" alt="" />
    </div>
     <div class="rowItems">
    <h3>
      {{ product.desc }} <br />
      מחיר: {{ product.price }} 
    </h3>
    </div>
  
    <hr />
    <div class="rowItems">
      <ProductForm />
    </div>
  </div>
</template>

<script>
import ProductForm from "../components/ProductForm";

export default {
  name: "About",
  components: {
    ProductForm,
  },
  data() {
    return {
      product: [],
      NoImageText: "No Image",
    };
  },
  created() {
    this.product = JSON.parse(this.$route.params.data);
    console.log("about=>" + this.product.id);
  },
  methods: {
    navigate() {
      router.go(-1);
    },
  },
};
</script>

<style scoped>
.about {
  display: flex;
  align-items: center;
  flex-wrap: wrap;
}
#Image {
  border-radius: 8px;
  width: 10rem;
  
   
}
.rowItems{
  flex-direction: row;
  width: 100%;
direction: rtl;
}
#back{
  height: 5rem;
}

</style>
