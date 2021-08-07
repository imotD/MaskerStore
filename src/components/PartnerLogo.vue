<template>
  <div>
    <div class="partner-logo">
      <div class="container">
        <carousel
          class="logo-carousel"
          :loop="true"
          :autoplay="true"
          :items="5"
          :dots="false"
          :nav="false"
        >
          <div class="logo-item">
            <div class="tablecell-inner">
              <img src="img/logo-carousel/logo-1.png" alt="brand-logo" />
            </div>
          </div>
          <div class="logo-item">
            <div class="tablecell-inner">
              <img src="img/logo-carousel/logo-2.png" alt="brand-logo" />
            </div>
          </div>
          <div class="logo-item">
            <div class="tablecell-inner">
              <img src="img/logo-carousel/logo-3.png" alt="brand-logo" />
            </div>
          </div>
          <div class="logo-item">
            <div class="tablecell-inner">
              <img src="img/logo-carousel/logo-4.png" alt="brand-logo" />
            </div>
          </div>
          <div class="logo-item">
            <div class="tablecell-inner">
              <img src="img/logo-carousel/logo-5.png" alt="brand-logo" />
            </div>
          </div>
        </carousel>
      </div>
    </div>
  </div>
</template>

<script>
import carousel from "vue-owl-carousel";

export default {
  name: "PartnerLogo",
  components: {
    carousel,
  },
};
</script>

<style scoped>
</style>