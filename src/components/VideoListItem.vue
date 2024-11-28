<template>
    <li class="videoItem" @click="onVideoSelect">
        <img class="videoImg" :src="imageUrl" alt="">
        <div>{{ video.snippet.title}}</div>
    </li>
</template>


<script>
export default {
    name: 'VideoListItem',
    emits: ['videoSelect'],
    props: ['video'],
    computed: {
        imageUrl(){
            return this.video.snippet.thumbnails.medium.url
        }
    },
    methods: {
        onVideoSelect(){
            this.$emit('videoSelect', this.video)
        }
    }
}
</script>

<style>
.videoItem{
    display: flex;
    margin: 20px ;
    border: 1px solid green;
    border-radius: 30px;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
    align-items: center;
}
.videoImg{
    border-radius: 30px 0px 0px 30px;
    margin-right: 30px;
}
</style>