<template>
  <div>
    <section class="hero-section">
      <carousel class="hero-items" :items="1" :nav="false" :autoplay="true">
        <div
          v-for="(slide, i) in items"
          :key="i"
          class="single-hero-items set-bg"
          :style="`background-image: url(img/${slide.img}.jpg)`"
        >
          <div class="container">
            <div class="row">
              <div class="col-lg-6">
                <span>{{ slide.tag }}</span>
                <h1>{{ slide.title }}</h1>
                <p>
                  Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed
                  do eiusmod tempor incididunt ut labore et dolore
                </p>
                <a href="#" class="primary-btn">Shop Now</a>
              </div>
            </div>
          </div>
        </div>
      </carousel>
    </section>
  </div>
</template>

<script>
import carousel from "vue-owl-carousel";

export default {
  name: "HeroSlideShow",
  components: {
    carousel,
  },
  data() {
    return {
      items: [
        {
          tag: "Bag, kids",
          title: "Black Friday",
          img: "hero-2",
        },
        {
          tag: "Shoes, sale",
          title: "Flash Sale",
          img: "hero-1",
        },
        {
          tag: "T-shirt, pants",
          title: "Promo Hut 17",
          img: "hero-3",
        },
      ],
    };
  },
};
</script>

<style scoped>
</style>