<template>
  <div>
    <div id="player"></div>
    <div class="info" v-if="video">
      <h4 v-html="video.title" />
      <hr />
      <p v-html="video.description" />
    </div>
  </div>
</template>

<script>
export default {
  name: "VideoDetail",
  props: ["video"],
  data() {
    return {};
  },
  mounted() {
    console.log("mounted");
    var tag = document.createElement("script");

    tag.src = "https://www.youtube.com/iframe_api";
    var firstScriptTag = document.getElementsByTagName("script")[0];
    firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

    // eslint-disable-next-line no-unused-vars
    window.onYouTubeIframeAPIReady = () => {
      console.log("YT Loaded");
      try {
        window.player = new window.YT.Player("player", {
          width: "100%",
          videoId: "M7lc1UVf-VE",
        });
      } catch(e) {
        console.log("Just ignore this:")
        console.log(e)
      }
    };
  },
};
</script>

<style></style>
