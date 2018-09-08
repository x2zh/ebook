<template>
    <div id="app">
        <el-container>
            <el-header>
                {{book_title}}
                <div id="nav">
                    <router-link to="/">Home</router-link>
                    |
                    <router-link to="/about">About</router-link>
                </div>
            </el-header>
            <el-container>
                <el-aside width="400px">
                    <el-tree
                            :data="catalog"
                            :props="defaultProps"
                            accordion
                            @node-click="handleNodeClick"></el-tree>
                </el-aside>
                <el-container>
                    <el-main>
                        <router-view/>
                    </el-main>
                </el-container>
            </el-container>
        </el-container>
    </div>
</template>

<script>
    import HelloWorld from "@/components/HelloWorld.vue";
    import book_info from "@/assets/book-info.json";

    export default {
        name: "app",
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


<style>
</style>
