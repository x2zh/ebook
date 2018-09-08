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
    // @ is an alias to /src
    import HelloWorld from "@/components/HelloWorld.vue";
    import book_info from "@/assets/book-info.json";

    export default {
        name: "home",
        data() {
            return {
                video_url: "https://vibook.oss-cn-beijing.aliyuncs.com/video/1-1-1.mp4",
                video_title: "",
                video_base_url: book_info.video_base_url,
                video_url_suffix: book_info.video_url_suffix,
                book_title: book_info.title,
                catalog: book_info.units,
                book_info: book_info.units,
                defaultProps: {
                    children: "children",
                    label: "label"
                }
            };
        },
        methods: {
            handleNodeClick(e) {
                console.log(e);
                if (e.id) {
                    this.video_url = this.video_base_url + e.id + "-1" + this.video_url_suffix;
                    this.video_title = e.label;
                }
            },
            change_video(e) {
                console.log(e);
            }
        },

        components: {
            HelloWorld
        }
    };
</script>
