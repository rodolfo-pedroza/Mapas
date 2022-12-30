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
let myImg = cld.image('hotspot/2016/Enero')

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
  props: ['cat','year','month'],
  methods: {
    log() {

      let imgName = '';
      if (this.month != null) {
        imgName = this.cat+'/'+this.year+'/'+this.month        
      }else{
        imgName = this.cat+'/'+this.year        
      }    

      console.log(imgName)

      this.myImg = myImg = cld.image(imgName).resize(scale().height(620));
    }
  }
};
</script>

<!-- Render the image in a Vue.js component. -->
<template>
  <div>
    <AdvancedImage :cldImg="myImg" />
  </div>
</template>