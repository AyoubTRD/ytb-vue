<template>
  <li>{{ video.title }}</li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: {
    video: Object
  }
};
</script>

<style>
</style>