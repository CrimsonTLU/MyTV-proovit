<script>
import { createApi } from 'unsplash-js';
import VueSlickCarousel from 'vue-slick-carousel';
import 'vue-slick-carousel/dist/vue-slick-carousel.css';
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css';
import VueFullscreen from 'vue-fullscreen';
import Vue from 'vue';
import { ref, computed } from 'vue';

Vue.use(VueFullscreen);

const unsplash = createApi({ accessKey: process.env.api_key });

export default {
  name: 'IndexPage',
  components: {
    VueSlickCarousel
  },
  data() {
    return {
      photos: []
    }
  },
  computed: {
    imageUrl() {
      return (id) => {
        return "https://source.unsplash.com/" + id;
      }
    }
  },
  mounted() {
    unsplash.photos.getRandom({
      count: 5,
    }).then(result => {
      if (result.errors) {
        console.log('error occurred: ', result.errors[0]);
      } else {
        this.photos = result.response;
        console.log(this.photos[3].id);
      }
    });
  }
}
</script>

<template>
  <div>
    <template v-if="photos.length">
      <VueSlickCarousel id="imagecarousel" :arrows="true" :dots="false" :autoplay="true" :adaptiveHeight="true">
        <div v-for="photo in photos" :key="photo.id" id="image-wrapper" class="w-screen h-screen overflow-x-hidden overflow-y-auto">
          <img :src="imageUrl(photo.id)">
        </div>
        
      </VueSlickCarousel>
    </template>
    <img v-else>
  </div>
</template>
