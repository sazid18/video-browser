<template>
    <div>
        <SearchBar @termChange="onTermChange"/>
    </div>
</template>


<script>
import SearchBar from './components/SearchBar';

// eslint-disable-next-line no-unused-vars
const API_KEY = process.env.YOUTUBE_API_KEY;

export default {
    name: 'App',
    components:{
        SearchBar
    },
    methods: {
        onTermChange(searchTerm) {
            console.log("input changed")
            console.log(searchTerm)
        }
    }
};
</script>
