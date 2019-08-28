<template>
    <div v-if="video" class="mx-4">
        <div class="embed-responsive embed-responsive-16by9"> 
            <iframe :src="videoUrl" class="embed-responsive-item"/>
        </div>
        <h3>{{video.snippet.title}}</h3>
        <p>
            {{video.snippet.description}}
        </p>
    </div>
</template>

<script>
    export default {
        props: ['video'],
        computed: {
            videoUrl(){
                const { videoId } = this.video.id

                return `https://www.youtube.com/embed/${videoId}`; 
            }
        }
    }
</script>

<style scoped>

</style>