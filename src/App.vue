<template>
  <div id="app" class="conatainer">
    <div class="row mr-auoto text-center my-4">
      <app-search-bar @termChange="onTermChange"></app-search-bar>
    </div>

    <div class="row mx-2">
      <div class="col-md-8">
        <app-video-detail :video="selectedVideo"></app-video-detail>
      </div>
      <div class="col-md-4">
        <app-video-list :videos="videos" @videoSelect="onVideoSelect"></app-video-list>
      </div>
    </div>
  
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue'
import VideoList from './components/VideoList.vue'
import VideoDetail from './components/VideoDetail.vue'

const API_KEY = 'AIzaSyCHvHm1R2iAyl9URkbAwWbQ2H3t9O0gHBc';

export default {
  name: 'app',
  components: {
    appSearchBar: SearchBar,
    appVideoList: VideoList,
    appVideoDetail: VideoDetail,
  },
  data() {
    return {
      videos: [],
      selectedVideo: null
    }
  },
  methods: {
    onVideoSelect(video){
      this.selectedVideo = video;
    },
    onTermChange(searchTerm){
      axios.get('https://www.googleapis.com/youtube/v3/search',{
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: searchTerm
        }
      })
      .then( response => {
        console.log(response.data);
        this.videos = response.data.items; 
      })
      .catch(err => { console.log(err); });
    }
  }
}
</script>

<style scoped>

</style>
