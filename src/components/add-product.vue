<template>
  <div>
      <h1 class="title">Ürün Ekleme Uygulaması</h1>
    <hr />
    <div class="container">
      <div class="image">
        <img :src="previewImage" width="160px" height="160px" />
        <button class="btn btn-outline-secondary mt-2" @click="chooseImg()">
          Resim Seç
        </button>
        <input
          type="file"
          @change="uploadImage"
          ref="selectImg"
          v-show="false"
        />
      </div>
      <div class="add">
        <div class="row">
          <div class="col-md-12"></div>
          <label for="name">Ürün Adı </label>
          <div class="input-group">
            <input
              type="text"
              class="form-control"
              name="name"
              v-model="entity.name"
              aria-label="Ürün Adı"
            />
          </div>
        </div>

        <div class="row">
          <div class="col-md-6">
            <label for="price">Ürün Fiyatı </label>
            <div class="input-group">
              <input
                type="text"
                class="form-control"
                name="price"
                v-model="entity.price"

                aria-label="Ürün Adı"
              />
            </div>
          </div>
          <div class="col-md-6">
            <label for="qua">Ürün Adeti </label>
            <div class="input-group">
              <input
                type="text"
                class="form-control"
                name="qua"
                v-model="entity.quantity"

                aria-label="Ürün Adı"
              />
            </div>
          </div>

        </div>
        <div class="row">
         <div class="col-md-12">
          <button class="btn btn-secondary mt-5" @click="addProduct" style="width: 100%">Ekle</button>
          </div>
          </div>
      </div>
    </div>
  </div>
</template>

<script>
import {eventBus} from '../main';


export default {
  data() {
    return {
      counter: 0,
      entity: {},
      previewImage: 'https://www.generationsforpeace.org/wp-content/uploads/2018/03/empty-300x240.jpg',
      productList: []
    };
  },
  components: {
  },
  methods: {
    chooseImg() {
      this.$refs.selectImg.click();
    },
    uploadImage(e) {
      const image = e.target.files[0];
      const reader = new FileReader();
      reader.readAsDataURL(image);
      reader.onload = e => {
        this.previewImage = e.target.result;
      };
    },
    addProduct() {
      if (this.productList.length === 10) return;
      this.entity.previewImage = this.previewImage;
      const maxId = Math.max(...this.productList.map(data => data.id)) < 0 ? 0 : Math.max(...this.productList.map(data => data.id));
      const id = maxId + 1;
      this.entity.id = id;
      this.productList.push(this.entity);
      console.log(this.productList);
      eventBus.$emit('product-list',this.productList);
      console.log("id =>",this.entity.id)
      this.entity = {}
    }
  },
  mounted: () => {}
};
</script>

<style scoped>
.container {
  display: flex;
  width: 70%;
}
.image {
  padding: 20px;

    box-shadow: 0 1px 5px 0 rgb(0 0 0 / 15%);

  flex: 1;
  margin-right: 40px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.add {
  padding: 20px;
    box-shadow: 0 1px 5px 0 rgb(0 0 0 / 15%);

  flex: 2;
}
</style>
