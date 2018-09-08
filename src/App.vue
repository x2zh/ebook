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
                        <router-view></router-view>
                    </el-main>
                </el-container>
            </el-container>
        </el-container>
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
                }
            };
        },
        methods: {
            handleNodeClick(e) {
                console.log(e);
                if (e.id) {
                    this.$router.push(`/${e.id}`)
                }
            },
        },
        components: {
            player
        }
    };
</script>


<style>
</style>
