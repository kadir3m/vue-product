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
  </div>
</template>

<script>
export default {
    props: ['product'],

}
</script>

<style scoped>
.k-card {
    width: 180px;
    height: 240px;
    display: flex;
    flex-direction: column;
    padding: 4px;
    box-shadow: 0 1px 5px 0 rgb(0 0 0 / 15%);

 
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