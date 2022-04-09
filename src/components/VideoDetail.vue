<template>
  <div v-if="video" class="col-md-8">
    <div class="embed-responsive embed-responsive-16by9">
      <iframe class="embed-responsive-item" :src="videoUrl" allowfullscreen > </iframe>
    </div>
    <div class="details">
      <h4>{{ video.snippet.title }}</h4>
      <p>{{ video.snippet.description }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "VideoDetail",
  props: ["video"],
  computed: {
    videoUrl() {
      const videoId = this.video.id.videoId;
      const baseUrl = "https://www.youtube.com/embed";
      return `${baseUrl}/${videoId}`;
    },
  },
};
</script>

<style scoped>
.details {
  margin: 10px 0;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>
