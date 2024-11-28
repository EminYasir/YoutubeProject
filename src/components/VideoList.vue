<template>
    <ul class="videoList">
        <VideoListItem @videoSelect="onVideoSelect" v-for="video in videos" :key="video.etag" :video="video" />
    </ul>
</template>

<script>
import VideoListItem from './VideoListItem.vue';

export default {
    name: 'VideoList',
    props: ['videos'],
    emits: ['videoSelect'],
    components: {
        VideoListItem
    },
    methods: {
        onVideoSelect(video) {
            this.$emit('videoSelect', video)
        }
    }
}
</script>

<style scoped>
.videoList {
    list-style: none;
    width: 100%;
}
</style>