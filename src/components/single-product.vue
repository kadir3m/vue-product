<template>
  <div class="k-card">
<div class="k-card-img">
<img style="width: 170px; height: 120px" :src="product.previewImage">
</div>
<div class="k-card-container">
<span>{{product.name}}</span>
<span>{{product.price}}</span>
<span>{{product.quantity}}</span>
</div>
<div class="close" @click="deleteProduct(product.id)">X</div>
  </div>
</template>

<script>
import {eventBus} from '../main'
export default {
    props: ['product'],
    methods: {
        deleteProduct(id) {
        this.$emit('deletedId', id);
        console.log("1");
        }
    },
    data: () => {
return {
}
    }
}
</script>

<style scoped>
.k-card {
    width: 180px;
    height: 240px;
    display: flex;
    flex-direction: column;
    padding: 4px;
    margin: 10px;
    position: relative;
    box-shadow: 0 1px 5px 0 rgb(0 0 0 / 15%);
   
 
}
.k-card .close {
    display: none;
}
.k-card:hover .close {
    background-color: red;
    display: flex;
    justify-content: center;
    width: 20px;
    align-items: center;
    height: 20px;
    border-radius: 50%;
    color: white;
    position: absolute;
    top: -7px;
    right: -7px;
    display: flex;
}
.k-card:hover {
    background-color: rgba(150, 206, 255, 0.56);
    cursor: pointer;
}
.k-card .k-card-img {
        flex: 1.5;
}
.k-card .k-card-container {
        flex: 2;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;

}
</style>