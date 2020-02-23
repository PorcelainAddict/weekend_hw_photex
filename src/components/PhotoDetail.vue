<template lang="html">
  <div class="photodetail" v-if="photo">
    <h3 id="title">{{photo.author}}</h3>
    <img id="photo" :src=photo.download_url>
    <h6>Find me at:
      {{photo.url}}
    </h6>
    <!-- <form v-on:submit.prevent="saveCritique">
      <label for="critique-input">Add Critique:</label>
      <input type="text" id="critique-input" v-model="newCritique.comment"/>
      <input type="submit" value="Save Critique"/>
    </form>
    <ul>
      <li v-for="critique in critiques">{{critique.comment}}</li>
    </ul> -->
  </div>
</template>



<script>
import {eventBus} from '../main.js'

export default {
  name: 'PhotoDetail',
  data() {
    return {
      photo: null,
    }
    // critiques: []
    // newCritique: {
    //   comment: ""
    // }
  },
  // methods: {
  //   saveCritique: function() {
  //     this.critique.push(this.newCritique);
  //     this.newCritique = {
  //       comment: ""
  //     }
  //   }
  // },
  mounted() {
    eventBus.$on("photo-selected", (photo) =>
    this.photo = photo)
  }
}
</script>

<style lang="css" scoped>

.photodetail {
  position: fixed;
  top: 20px;
  right: 50px;
}



#photo {
  height: 500px;
  width: 700px;
}
</style>
