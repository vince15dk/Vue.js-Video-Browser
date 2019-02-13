<template>
<ul class ="list-group col-md-4">
    <VideoListItem
    v-for="eachVideo in videos"
    :video="eachVideo"
    :key="eachVideo.etag"
    @videoSelect="onVideoSelect"
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
    props: ['videos'],
    methods: {
        onVideoSelect(video){
            this.$emit('videoSelect', video);
        }
    }
};
</script>

<style>

</style>