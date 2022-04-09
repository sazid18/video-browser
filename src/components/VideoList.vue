<template>
    <ul class="list-group col-md-4">
        <VideoListItem
            v-for="(video) in videos"
            :video="video"
            :key="video.etag"
            @videoSelect="onVideoSelect"
        >
        </VideoListItem>
    </ul>
</template>

<script>
import VideoListItem from './VideoListItem.vue';

export default {
    name: 'VideoList',
    // props: ['videos']
    props: {
        videos: Array   // type check
    },
    components: {
        VideoListItem
    },
    methods: {
        onVideoSelect: function(videoData) {
            this.$emit('videoSelect', videoData);
        }
    }
}
</script>

<style>

</style>