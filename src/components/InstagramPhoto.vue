<template>
  <div>
    <div class="instagram-photo">
      <div
        v-for="i in 6"
        :key="i"
        class="insta-item set-bg"
        :style="`background-image: url('img/insta-${i}.jpg')`"
      >
        <div class="inside-text">
          <i class="ti-instagram"></i>
          <h5><a href="#">@gudangmasker.id</a></h5>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "InstagramPhoto",
};
</script>

<style lang="scss" scoped>
</style>