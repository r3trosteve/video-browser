<template lang="html">
  <li class="list-group-item media" @click="onVideoSelect">
    <img :src="thumbnailUrl" alt="" class="mr-3">
    <div class="media-body">
      <h5>{{ video.snippet.title }}</h5>
      <!-- {{ video.snippet.}} -->
    </div>
  </li>
</template>

<script>
export default {
  name: 'VideoListItem',
  props: {
    video: Object
  },
  methods: {
    onVideoSelect() {
      this.$emit('videoSelect', this.video);
    }
  },
  computed: {
    thumbnailUrl() {
      return this.video.snippet.thumbnails.default.url;
    }
  }
}
</script>

<style lang="css" scoped>
  li {
    display: flex;
  }
  li:hover {
    color: #eee;
    cursor: crosshair;
  }
</style>
