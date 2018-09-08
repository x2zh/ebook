<template>
    <div class="home">
        <h1>{{video_title}}</h1>
        <video :src=video_url controls="controls">您的浏览器不支持 video 标签。</video>
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
                video_title: "hello",
                pointer: "1",
            }
        },
        methods: {
            change_video(e) {
                this.pointer = e;
            },
        },
        computed:{
            video_url: function () {
                return `https://vibook.oss-cn-beijing.aliyuncs.com/video/${this.id}-${this.pointer}.mp4`;
            }
        },
        props: ["id",],
    };
</script>
