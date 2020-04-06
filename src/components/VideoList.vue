<template>
  <ul>
    <div class="col s12" v-for="video in videos" :key="video.videoId">
      <VideoListItem :video="video" @playVideo="onPlayVideo" />
    </div>
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem";

export default {
  name: "VideoList",
  props: {
    videos: Array,
  },
  components: {
    VideoListItem,
  },
  methods: {
    onPlayVideo(video) {
      this.$emit("playVideo", video);
    },
  },
};
</script>

<style scoped>
ul {
  max-height: calc(100vh - 140px);
  overflow-y: scroll;
  overflow-x: hidden;
}
</style>
