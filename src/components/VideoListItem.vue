<template>
    <div>

        <li class="list-group-item media" @click="onVideoSelect">
            <img class="mr-3" :src="thumbnailUrl" alt="video thumbnail">
            <div class="media-body">
                {{video.snippet.title}}
            </div>
        </li>


    </div>
</template>

<script>
    export default {
        name:'VideoListItem',
        props:{
            video:Object
        },
        methods:{
            onVideoSelect(){
                this.$emit('videoSelect', this.video)
            }
        },
        computed:{
            thumbnailUrl(){
                return this.video.snippet.thumbnails.default.url;
            }
        }
    }
</script>

<style scoped>
    li{
        display: flex;
        cursor: pointer;
    }
    li:hover{
        background-color: rgba(126, 126, 126, 0.411);
    }
</style>