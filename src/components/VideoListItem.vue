<template>
  <li>
    <div class="card">
      <div class="card-image">
        <img :src="video.thumbnails.high.url" />
        <span class="card-title" v-html="video.channelTitle" />
        <a
          class="btn-floating btn-medium halfway-fab waves-effect waves-light red"
        >
          <i class="material-icons" @click="onClick">play_arrow</i>
        </a>
      </div>
      <div class="card-content">
        <p>{{ video.title }}</p>
      </div>
    </div>
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: {
    video: Object,
  },
  methods: {
    onClick() {
      this.$emit("playVideo", this.video);
    },
  },
};
</script>

<style></style>
