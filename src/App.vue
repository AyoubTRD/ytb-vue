<template>
  <div>
    <SearchBar @termChange="handleSearch" />
    <div class="container">
      <div class="row">
        <div class="col s12 m8">
          <VideoDetail :video="video" />
        </div>
        <div class="col s12 m4">
          <VideoList :videos="videos" @playVideo="onPlayVideo" />
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

const API_KEY = "AIzaSyCavhwsTKqVzb4nj89nyQqN3cLIBWaK_Ec";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList,
    VideoDetail,
  },
  data() {
    return {
      videos: [],
      video: 0,
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
            maxResults: 30,
          },
        }
      );
      this.videos = res.data.items.map((item) => ({
        ...item.snippet,
        videoId: item.id.videoId,
      }));
    },
    onPlayVideo(video) {
      this.video = video;
      console.log(this.video.videoId);
      if (window.player) {
        console.log("updating the id");
        window.player.loadVideoById(this.video.videoId);
      }
    },
  },
};
</script>

<style>
html {
  font-family: Arial, Helvetica, sans-serif;
}
</style>
