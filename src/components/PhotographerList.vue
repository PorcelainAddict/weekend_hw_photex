<template lang="html">
  <div class="photographer-list">
    <ul>
      <li id="photographerList" v-on:change="handleChange" v-model="selectedPhoto">
        <photographer-item v-for="(photo, index) in photos"
        :photo="photo"
        :value="photo"
        :key="index"
        >
      </photographer-item>
    </li>
  </ul>
</div>
</template>

<script>
import PhotographerItem from "@/components/PhotographerItem";
import { eventBus } from '../main.js'

export default {
  name: "photographer-list",
  props: ["photos"],
  components: {
    "photographer-item": PhotographerItem
  },
  data() {
    return {
      "selectedPhoto": {},
    }
  },
  methods: {
    handleChange() {
      eventBus.$emit('photo-selected', this.selectedPhoto);
    }
  }
};
</script>

<style lang="css" scoped>
.photographer-list {
  font-family: helvetica;
  list-style: none;
}
</style>
