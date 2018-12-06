<template>
    <div class="home">
        <h1>文型:  {{video_title}}</h1>
        <video controls autoplay :src="video_url">
        </video>
        <el-pagination
                background
                layout="prev, pager, next"
                @current-change=change_video
                @prev-click=change_video
                @next-click=change_video
                :total="40">
        </el-pagination>
    </div>
</template>

<script>
    export default {
        name: "player",
        data() {
            return {
                pointer: "1",
            }
        },
        methods: {
            change_video(e) {
                this.pointer = e;
            },
        },
        computed: {
            video_url: function () {
                return `https://vibook.oss-cn-beijing.aliyuncs.com/video/${this.id}-${this.pointer}.mp4`;
            }
        },
        props: ["id","video_title"],
        beforeCreate() {
            this.pointer = "1";
        }
    };
</script>

<style>
    video {
        object-fit: fill;
        width: 100%;
        /*height: 400px;*/
    }
    .home {
        padding: 0 10vw 0 5vw;
    }
</style>
