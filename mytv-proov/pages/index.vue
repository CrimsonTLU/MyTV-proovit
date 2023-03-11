
<template>
  <div>
    <VueSlickCarousel :arrows="true" :dots="false">
      <img v-for="(item, index) in photo">
      "https://source.unsplash.com/"{{ photo.id }}

      <img src="https://source.unsplash.com/random/" alt="2">
      <img src="https://source.unsplash.com/random/" alt="3">
      <img src="https://source.unsplash.com/random/" alt="4">
      <img src="https://source.unsplash.com/random/" alt="5">
    </VueSlickCarousel>
  </div>
</template>

<script>

import { createApi } from 'unsplash-js';
import VueSlickCarousel from 'vue-slick-carousel'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'

const unsplash = createApi({ accessKey: 'N9S1GGf41Brm-VGvExB46hqwv2QbGnC82NUVKVVFQng' });

unsplash.photos.getRandom({
  count: 5,
}).then(result => {
  if (result.errors) {

    console.log('error occurred: ', result.errors[0]);
  } else {

    const photo = result.response;
    console.log(photo[0].id);
    return {
      photo: photo
    }
  }
});

export default {
  name: 'IndexPage',
  components: { VueSlickCarousel },
}
</script>
