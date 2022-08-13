<template>
  <div class="home">
    <Header
      :cart="keranjangUser"
      @removeItem="deleteItem"
      @checkout="checkout"
    />
    <HeroSlideShow />
    <WomenStyle @saveKeranjang="saveCart" />
    <InstagramPhoto />
    <PartnerLogo />
    <Footer />
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";
// @ is an alias to /src
import Header from "@/components/Header.vue";
import HeroSlideShow from "@/components/HeroSlideShow.vue";
import WomenStyle from "@/components/WomenStyle.vue";
import InstagramPhoto from "@/components/InstagramPhoto.vue";
import PartnerLogo from "@/components/PartnerLogo.vue";
import Footer from "@/components/Footer.vue";
import axios from "axios";

export default {
  name: "Home",
  components: {
    Header,
    HeroSlideShow,
    WomenStyle,
    InstagramPhoto,
    PartnerLogo,
    Footer,
  },
  mounted() {
    if (localStorage.getItem("keranjangUser")) {
      try {
        this.keranjangUser = JSON.parse(localStorage.getItem("keranjangUser"));
      } catch (e) {
        localStorage.removeItem("keranjangUser");
      }
    }
  },
  data() {
    return {
      keranjangUser: [],
      message: "",
    };
  },
  methods: {
    checkout() {
      let productIds = this.keranjangUser.map(function (product) {
        return product.id;
      });

      let checkoutData = {
        name: this.customerInfo.name,
        email: this.customerInfo.email,
        number: this.customerInfo.number,
        address: this.customerInfo.address,
        transaction_total: this.totalBiaya,
        transaction_status: "PENDING",
        transaction_details: productIds,
      };

      axios
        .post(
          "http://shayna-backend.belajarkoding.com/api/checkout",
          checkoutData
        )
        .then(() => this.$router.push("Succes"))
        .catch((err) => console.log(err));
    },
    deleteItem(index) {
      this.keranjangUser.splice(index, 1);
      const parsed = JSON.stringify(this.keranjangUser);
      localStorage.setItem("keranjangUser", parsed);
    },
    saveCart(product) {
      let productStored = {
        id: product.id,
        name: product.name,
        price: product.price,
        photo: product.galleries[0].photo,
      };

      this.keranjangUser.push(productStored);
      const parsed = JSON.stringify(this.keranjangUser);
      localStorage.setItem("keranjangUser", parsed);
      window.scrollTo(0, 0);
    },
  },
};
</script>
