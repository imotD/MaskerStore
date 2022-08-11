<template>
  <div class="home">
    <Header :cart="keranjangUser" @removeItem="deleteItem" />
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
    };
  },
  methods: {
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
