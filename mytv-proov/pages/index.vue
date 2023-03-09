
<template>
  <div>
    <VueSlickCarousel :arrows="true" :dots="false">
      <div>1</div>
      <div>2</div>
      <div>3</div>
      <div>4</div>
    </VueSlickCarousel>
  </div>
</template>

<script>
import VueSlickCarousel from 'vue-slick-carousel'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'

export default {
  name: 'IndexPage',
  components: { VueSlickCarousel },
}
</script>
