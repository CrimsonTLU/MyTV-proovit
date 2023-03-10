
<template>
  <div>
    <VueSlickCarousel :arrows="true" :dots="false">
      <img src="https://source.unsplash.com/random/" alt="1">
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

// non-feed example

unsplash.photos.getRandom({
  count: 5,
}).then(result => {
  if (result.errors) {
    // handle error here
    console.log('error occurred: ', result.errors[0]);
  } else {
    // handle success here
    const photo = result.response;
    console.log(photo);
  }
});

export default {
  name: 'IndexPage',
  components: { VueSlickCarousel },
}
</script>
