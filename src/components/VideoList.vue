<template>
    <ul class="list-group list-unstyled mx-2"> 
        <app-video-list-item 
            v-for="video in videos" 
            :key="video.etag" 
            :video="video"
            @viseoSelect="onVideoSelect"
        ></app-video-list-item>

        
    </ul>
</template>

<script>
    import VideoListItem from './VideoListItem';
    export default {
        name: 'VideoList',
        props: ['videos'],
        components: {
            appVideoListItem: VideoListItem,
        },
        methods: {
            onVideoSelect(video){
                this.$emit('videoSelect', video);
            }
        }
    }
</script>

<style scoped>
    li {
        display: flex;
    }
</style>