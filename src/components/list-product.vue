<template>
  <div>
    <h3 class="title">Eklenen Ürünlerin Listesi</h3>
    <hr>
    <div class="list">
       <slot name="kadir"></slot>
       <p></p>
    </div>
   
  </div>
</template>

<script>
export default {
  props: ['list'],
  components: {
  },
  data: () => {
return {
}
  },

  created: function() {
    console.log("list =>", this.list)
  },
  // watch: {
  //   list: function (value) {
  //   console.log("list =>", value)

  //   }
  // }
};
</script>

<style scoped>
.list {
margin-left: 30px;
    flex-wrap: wrap;
    justify-content: center;
    display: flex;
}
</style>
