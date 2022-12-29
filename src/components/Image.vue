<script>
import { AdvancedImage } from '@cloudinary/vue';
import { Cloudinary } from '@cloudinary/url-gen';
import { scale } from '@cloudinary/transformation-builder-sdk/actions/resize';

// Create a Cloudinary instance and set your cloud name.
const cld = new Cloudinary({
  cloud: {
    cloudName: 'dtrkstqmm',
  },
});

// Instantiate a CloudinaryImage object for the image with the public ID, 'docs/models'.
let myImg = cld.image('Coropletas_AQI/2016/Mayo2')

myImg.resize(scale().height(620));



export default {
  components: {
    AdvancedImage,
  },
  data() {
    return {
      myImg,
    };
  },
};
</script>

<!-- Render the image in a Vue.js component. -->
<template>
  <div class="container">
    <div class="mx-auto text-center">
      <AdvancedImage :cldImg="myImg" />
    </div>
  </div>
</template>