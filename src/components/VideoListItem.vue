<template>
  <li class="media" @click="onVideoItemClick">
    <img :src="thumbnailsUrl" class="mr-3" />
    <div class="media-body">
      <h5 class="mt-0 mb-1">
        {{ video.snippet.title }}
      </h5>
      <p>
        {{ video.snippet.description }}
      </p>
    </div>
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: {
    video: Object,
  },
  computed: {
    thumbnailsUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
  },
  methods: {
    onVideoItemClick() {
      console.log("emit videoListItem");
      this.$emit("videoSelect", this.video);
    },
  },
};
</script>

<style>
li:hover {
  background-color: aliceblue;
  cursor: pointer;
}
</style>
