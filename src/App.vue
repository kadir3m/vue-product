<template>
  <div id="app">
    <addProduct></addProduct>
    <progressbar :percentage="percentage"></progressbar>
    <listProduct :list="product_list">
      <div slot="kadir" v-for="item in product_list" :key="item.id">
        <singleProduct @deletedId="deleteProduct" :product="item"></singleProduct>
      </div>
    </listProduct>
  </div>
</template>

<script>
import addProduct from "./components/add-product.vue";
import progressbar from './components/progressbar.vue';
import listProduct from './components/list-product.vue';
import singleProduct from './components/single-product.vue'


import {eventBus} from './main';
export default {
  components: {
    addProduct,
    progressbar,
    listProduct,
    singleProduct
  },

  data: () => {
    return {
      product_list : [],
      selectedComponent: "red-component",
      percentage: 0
    };
  },
  methods: {
        deleteProduct(id) {
      console.log("app =>", this.product_list);
       const i = this.product_list.map(data => data.id).indexOf(id);
       console.log("i=>>>>",i)
        this.product_list.splice(i,1);
        }
  },
    created: function() {
    eventBus.$on('product-list', (data) =>{
      this.product_list = data
      if(this.percentage >= 101)  return;
      this.percentage = this.product_list.length * 10;
    })
  },
   watch: {
    product_list: function (value) {
      console.log("app")
    if(this.percentage >= 101)  return;
      this.percentage = this.product_list.length * 10;

    }
  }
};
</script>

<style>
.title {
  text-align: center;
}
#app {
  margin: 30px;
}
</style>
