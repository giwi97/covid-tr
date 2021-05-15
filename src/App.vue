<template>
<div  class="tw-bg-scroll" :style="{'background-image': 'url(' +require('./assets/backg.jpg')+')'}">
  <Header />
  <div class="tw-container">
    <router-view />
  </div>
  <Footer />
</div>
</template>

<script>
import  Header  from "@/components/Header";
import Footer from "@/components/Footer";

export default {
  components: {
    Header,
    Footer
  },
};
</script>
