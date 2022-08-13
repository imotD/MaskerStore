<template>
  <div class="home">
    <header class="header-section">
      <div class="header-top">
        <div class="container">
          <div class="ht-left">
            <div class="mail-service">
              <i class="fa fa-envelope"></i>murah.masker@gudangmasker.id
            </div>
            <div class="phone-service">
              <i class="fa fa-phone"></i> +628 96510055
            </div>
          </div>
        </div>
      </div>
      <div class="container">
        <div class="inner-header">
          <div class="row">
            <div class="col-lg-2 col-md-2">
              <div class="logo">
                <a href="/">
                  <img
                    src="img/logo_website_shayna.png"
                    alt="logo-gudang-masker"
                  />
                </a>
              </div>
            </div>
            <div class="col-lg-7 col-md-7"></div>
            <div class="col-lg-3 text-right col-md-3">
              <ul class="nav-right">
                <li class="cart-icon">
                  Cart &nbsp;
                  <a href="#">
                    <i class="icon_bag_alt"></i>
                    <span> {{ cart.length }} </span>
                  </a>
                  <div class="cart-hover">
                    <div class="select-items">
                      <table>
                        <tbody v-if="cart.length > 0">
                          <tr v-for="(keranjang, index) in cart" :key="index">
                            <td class="si-pic">
                              <img
                                class="photo-item"
                                :src="keranjang.photo"
                                alt="img"
                              />
                            </td>
                            <td class="si-text">
                              <div class="product-selected">
                                <p>{{ keranjang.price }} x 1</p>
                                <h6>{{ keranjang.name }}</h6>
                              </div>
                            </td>
                            <td
                              @click="$emit('removeItem', index)"
                              class="si-close"
                            >
                              <i class="ti-close"></i>
                            </td>
                          </tr>
                        </tbody>
                        <tbody v-else>
                          <tr>
                            Cart Kosong
                          </tr>
                        </tbody>
                      </table>
                    </div>
                    <div class="select-total">
                      <span>total:</span>
                      <h5>${{ totalHarga }}.00</h5>
                    </div>
                    <div class="select-button">
                      <router-link to="/cart" class="primary-btn view-card">
                        VIEW CARD
                      </router-link>
                      <div
                        @click="$emit('checkout')"
                        class="primary-btn checkout-btn"
                      >
                        CHECK OUT
                      </div>
                    </div>
                  </div>
                </li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </header>
  </div>
</template>

<script>
export default {
  name: "Header",
  props: {
    cart: {
      type: Array,
      default: () => [],
    },
  },
  computed: {
    totalHarga() {
      return this.cart.reduce(function (items, data) {
        // console.log('keranjanguser', this.keranjangUser)
        // console.log("item", items);
        // console.log('data', data)
        return items + data.price;
      }, 0);
    },
  },
};
</script>

<style scoped>
.photo-item {
  height: 80px;
  width: 80px;
}
</style>