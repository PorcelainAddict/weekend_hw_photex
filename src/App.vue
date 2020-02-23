<template lang="html">
  <div id="app">
    <h1>Photex</h1>
    <photographer-list :photos="photos"></photographer-list>
    <photo-detail :photo='selectedPhoto'></photo-detail>
  </div>

</template>

<script>
import { eventBus } from './main.js';
import PhotographerList from './components/PhotographerList';
import PhotoDetail from './components/PhotoDetail';

export default {
  name: "app",
  components: {
    "photographer-list": PhotographerList,
    "photo-detail": PhotoDetail
  },
  data() {
    return {
      photos: [],
      selectedPhoto: null
    };
  },
  methods: {
    getPhotos: function() {
      fetch("https://picsum.photos/v2/list?page=2&limit=100")
      .then(res => res.json())
      .then(data => this.photos = data)
    }
  },
  mounted() {
    this.getPhotos();






  }
}
</script>

<style lang="css" scoped>

h1 {
  font-family: helvetica;
}
</style>
