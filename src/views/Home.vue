<template>
    <div class="home">
        <Header />
        <HeroSlideShow />
        <WomenStyle />
        <InstagramPhoto />
        <PartnerLogo />
        <Footer />
    </div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
// @ is an alias to /src
import Header from '@/components/Header.vue'
import HeroSlideShow from '@/components/HeroSlideShow.vue'
import WomenStyle from '@/components/WomenStyle.vue'
import InstagramPhoto from '@/components/InstagramPhoto.vue'
import PartnerLogo from '@/components/PartnerLogo.vue'
import Footer from '@/components/Footer.vue'

export default {
    name: 'Home',
    components: {
        Header,
        HeroSlideShow,
        WomenStyle,
        InstagramPhoto,
        PartnerLogo,
        Footer
    }
}
</script>
