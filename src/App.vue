<template>
  <div>
    <SearchBar @termChange="handleSearch" />
    <div class="container">
      <div class="row">
        <div class="col s12 m6">
          <VideoDetail />
        </div>
        <div class="col s12 m6">
          <VideoList :videos="videos" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VideoDetail";

import axios from "axios";

const API_KEY = "AIzaSyB8IAfuXNA0EJNcftDcuG3MBIorGcJCgrA";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    return {
      videos: []
    };
  },
  methods: {
    async handleSearch(term) {
      const res = await axios.get(
        "https://www.googleapis.com/youtube/v3/search",
        {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: term,
            maxResults: 30
          }
        }
      );
      this.videos = res.data.items.map(item => ({
        ...item.snippet,
        videoId: item.id.videoId
      }));
    }
  }
};
</script>

<style>
html {
  font-family: Arial, Helvetica, sans-serif;
}
</style>
