<template>

  <h4> <input type="text" v-model="search">חפש לפי מחיר</h4> 
  <div class="home" v-if="!isLoading">
        <div class="cat">
    <Categorise
      title="קטגוריות"
      :categorisTitle="storeCategoryTitles"
      @chosen-category="fillterByCategory"
    />
    </div>
    <div class="pro">
    <Products :productList="products" :filterProductList="productsByCategory" />
    </div>
  </div>
</template>

<script>
import Categorise from "../components/Categorise";
import axios from "axios";
import Products from "../components/Products";

export default {
  name: "Home",
  components: {
    Categorise,
    Products,
  },
  data() {
    return {
      title: "",
      products: [],
      isLoading: true,
      storeCategoryTitles: [],
      productsByCategory: [],
      search:''
    };
  },
  created: async function () {
    let res = await axios.get(
      "https://api.konimbo.co.il/v1/items?token=9c1a92bf8cefc59e4ec9fa7c53bba0f90dd8b15850bef1062dbf32c5e8fd3a08"
    );
    this.products = res.data;
    // this.productsToShow = res.data
    this.isLoading = false;
    this.storeCategoryTitles = new Set(
      res.data.map((item) => item.store_category_title)
    ); 
  },
  methods: {
    fillterByCategory(val) {
      this.productsByCategory=this.products.filter((item)=>item.store_category_title ===val)
    },
  },
  computed:{
    filteredPost(){
      return this.productsByCategory = products.filter((item)=>{return parseInt(item.price) <= parseInt(this.search)})
      
    }
  }
};
</script>

<style scoped>
.home{
  display: flex;
  direction: rtl;
}
.cat{
flex: 1;
border: 2px;
border-color: black;
}
.pro{
flex: 2;
}
</style>
