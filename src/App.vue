<template>
    <div class="container">
        <SearchBar @termChange="onTermChange"/>
        <VideoDetail
            :video="selectedVideo"
        />
        <VideoList 
            @videoSelect="onVideoSelect"
            :videos="videos"
        />
    </div>
</template>


<script>
import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList.vue';
import VideoDetail from './components/VideoDetail.vue';
import axios from 'axios';

const API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY;



export default {
    name: 'App',
    components:{
        SearchBar,
        VideoList,
        VideoDetail,
    },
    data() {
        return {
            videos: [],
            selectedVideo: null
        }
    },
    methods: {
        onTermChange(searchTerm) {
            axios
            .get('https://www.googleapis.com/youtube/v3/search',{
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            })
            .then(response => {
                this.videos = response.data.items
                console.log(response.data.items)
            })
        },
        onVideoSelect(videoData) {
            this.selectedVideo = videoData
        }

    }
};
</script>
