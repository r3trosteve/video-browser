<template>
  <div id="app" class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <div class="row">
      <VideoDetail :video="selected_video"></VideoDetail>
      <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
    </div>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue'
import VideoList from './components/VideoList.vue'
import VideoDetail from './components/VideoDetail.vue'
import axios from 'axios'
const API_KEY = 'AIzaSyA3lWMoSsW3qhXJ2I_8M-wzZ0V4SUcDLUI'

export default {
  name: 'app',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    return {
      videos: [],
      selected_video: null
    };
  },
  methods: {
    onTermChange(searchTerm) {
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          channelId: 'UCJupHVmDGk3Gk7f7T-3Aqww',
          q: searchTerm
        }
      })
      .then(response => {
        this.videos = response.data.items;
      });
    },
    onVideoSelect(video) {
      this.selected_video = video;
    }
  }
}
</script>

<style>
#app {

}
</style>
