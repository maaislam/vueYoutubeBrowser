<template>
    <div class="list-group">
        <VideoListItem 
            v-for = "video in videos" 
            :video = "video"
            :key="video.etag"
            @videoSelect="onVideoSelect">
        </VideoListItem>
    </div>
</template>

<script>

import VideoListItem from './VideoListItem'

    export default {
        name: 'VideoList',
        components:{
            VideoListItem
        },
        props: {
            videos:Array
        },
        methods:{
            onVideoSelect(video){
                this.$emit('videoSelect', video);
            }
        }
    };
</script>

<style scoped>

</style>