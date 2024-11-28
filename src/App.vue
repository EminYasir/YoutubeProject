<template>
  <div class="container">
    <h1 class="title">Youtube Uygulaması</h1>
    <SearchBar @searchInput="onSearchChance" />
    <div class="detailDiv">
      <VideoItemDetail :video="selectedVideo" />
      <VideoList @videoSelect="onVideoSelect" :videos="videos" />
    </div>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue'
import VideoList from './components/VideoList.vue'
import VideoItemDetail from './components/VideoItemDetail.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoItemDetail
  },
  data() {
    return {
      videos: [],
      selectedVideo:null,
    }
  },
  methods: {
    onSearchChance(searchValue) {
      this.selectedVideo = null;
      this.value = searchValue;
      console.log(this.value);
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params:
        {
          part: 'snippet', order: 'rating', type: 'video',
          key: 'AIzaSyDvpyt5jq59Co5Bxn0fN8fwoUg5GU_Xb-c',
          q: searchValue
        }
      }).then(res => this.videos = res.data.items)
        .catch(err => console.log(err.message))
    },
    onVideoSelect(video) {
      this.selectedVideo = video
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  max-width: 1200px;
  width: 100%;
  margin: 50px auto;
}

.title {
  text-align: center;
}

.detailDiv{
  display: flex;
}
</style>
