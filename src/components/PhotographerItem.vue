<template lang="html">
  <div class="photographlistitem" v-on:click="handleClick">
    <p>{{photo.author}}</p>

  </div>
</template>

<script>
import { eventBus } from '../main.js';
import PhotoDetail from '@/components/PhotoDetail';

export default {
  name: "photographer-item",
  props: ["photo"],
  methods: {
    handleClick(){
      eventBus.$emit('photo-selected', this.photo)
    }
  }
}
</script>

<style lang="css" scoped>


</style>
