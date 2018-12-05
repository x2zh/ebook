<template>
    <div id="app">
        <el-row>
            <el-col :span="24" class="header">
                <header style="text-align: center;">
                    <a href="javascript:void(0);"><h1>{{book_title}}</h1></a>
                </header>
            </el-col>
        </el-row>
        <el-row>
            <el-col :span="8" class="left">
                <el-tree
                        :data="catalog"
                        :props="defaultProps"
                        highlight-current
                        @node-click="handleNodeClick"></el-tree>
            </el-col>
            <el-col :span="16" class="right">
                <router-view :video_title="video_title"></router-view>
            </el-col>
        </el-row>
    </div>
</template>

<script>
    import player from "./views/Player";
    import book_info from "./assets/book-info.json";

    export default {
        name: "app",
        data() {
            return {
                book_title: book_info.title,
                catalog: book_info.units,

                defaultProps: {
                    children: "children",
                    label: "label"
                },
                video_title: "",
            };
        },
        methods: {
            handleNodeClick(e) {
                console.log(e);
                if (e.id) {
                    console.log(e);
                    this.$router.push(`/${e.id}`);
                    this.video_title = e.label;
                }
            },
        },
        components: {
            player
        }
    };
</script>


<style>
    #app {
        display: flex;
        justify-content: center;
        flex-direction: column;
    }

    body {
        padding: 0;
        border: 0;
        margin: 0;
    }

    .left {
        overflow-x: hidden;
        overflow-y: scroll;
        height: 80vh;
        margin-top: 2vh;
        padding-right: 4vw;
        box-shadow: 1px 0 0 0 ;
    }

    .left::-webkit-scrollbar {
        display: none;
    }

    .header {
        height: 15vh;
        border-radius: 2px 2px 2px 2px;
        box-shadow: 0 0 5px #000;
    }

    .right {
    }

    a {
        text-decoration: none;
        color: black;
    }
</style>
