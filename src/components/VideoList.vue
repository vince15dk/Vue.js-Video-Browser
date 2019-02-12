<template>
<ul>
    <VideoListItem 
    v-for="eachVideo in videos"
    :video="eachVideo"
    :key="eachVideo.etag"
    >

    </VideoListItem>
</ul>
</template>

<script>
import VideoListItem from './VideoListItem';

export default {
    name: 'VideoList',
    components: {
        VideoListItem
    },
    props: ['videos']
};
</script>

<style>
</style>