<template>
    <div>
        <SearchBar @termChange="onTermChange"/>
    </div>
</template>


<script>
import SearchBar from './components/SearchBar';
import axios from 'axios';

const API_KEY = process.env.VUE_APP_YOUTUBE_API_KEY;

export default {
    name: 'App',
    components:{
        SearchBar
    },
    methods: {
        onTermChange(searchTerm) {
            axios.get('https://www.googleapis.com/youtube/v3/search',{
                params: {
                    key: API_KEY,
                    type: 'video',
                    part: 'snippet',
                    q: searchTerm
                }
            })
        }
    }
};
</script>
