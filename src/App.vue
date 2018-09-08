<template>
    <div id="app">
        <header style="text-align: center;height: 15vh;">
            <h1>{{book_title}}</h1>
        </header>
        <div style="display: flex;flex-direction: row;justify-content: center;height: 85vh">
            <aside style="height: 100%;overflow-y: auto; width: 25vw; margin-right: 5vw;">
                <el-tree
                        :data="catalog"
                        :props="defaultProps"
                        highlight-current
                        @node-click="handleNodeClick"></el-tree>
            </aside>
            <main>
                <router-view></router-view>
            </main>
        </div>
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
</style>
