<template>
  <div>
    <section class="women-banner spad">
      <div class="container-fluid">
        <div class="row">
          <div class="col-lg-12 mt-5" v-if="products.length > 0">
            <carousel
              class="product-slider"
              :items="3"
              :nav="false"
              :autoplay="true"
              :dots="false"
            >
              <div
                class="product-item"
                v-for="itemProduct in products"
                :key="itemProduct.id"
              >
                <div class="pi-pic">
                  <img
                    style="object-fit: cover"
                    :src="itemProduct.galleries[0].photo"
                    alt="img"
                  />
                  <ul
                    style="cursor: pointer"
                    @click="$emit('saveKeranjang', itemProduct)"
                  >
                    <li class="w-icon active p-2 bg-warning">
                      <span><i class="icon_bag_alt text-white"></i></span>
                    </li>
                    <li class="quick-view p-2 font-weight-bolder">
                      <span> + Add to cart </span>
                    </li>
                  </ul>
                </div>
                <div class="pi-text">
                  <div class="catagory-name">{{ itemProduct.type }}</div>
                  <router-link :to="'/product/' + itemProduct.id">
                    <h5>{{ itemProduct.name }}</h5>
                  </router-link>
                  <div class="product-price">
                    ${{ itemProduct.price }}
                    <span>$35.00</span>
                  </div>
                </div>
              </div>
            </carousel>
          </div>
          <div class="col-lg-12" v-else>
            <p>Produk tidak tersedia</p>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import carousel from "vue-owl-carousel";
import axios from "axios";

export default {
  name: "WomenStyle",
  components: {
    carousel,
  },
  data() {
    return {
      products: [],
    };
  },
  mounted() {
    axios
      .get("http://shayna-backend.belajarkoding.com/api/products")
      .then((res) => (this.products = res.data.data.data))
      .catch((err) => console.log(err));
  },
};
</script>

<style scoped>
.product-item {
  margin-right: 25px;
}
</style>