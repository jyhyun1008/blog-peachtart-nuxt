<template>
    <div id="container">
        <h1 id="title">피치타르트 블로그</h1>
        <div v-for="category of categories">
            <a :href="`/${category}`"></a>
        </div>
        <div class="box-cont">
            뭔가 하나
        </div>
    </div>
</template>
<script setup>

import { marked } from 'marked';
//const route = useRoute()

var folderList = await $fetch(`https://api.github.com/repos/jyhyun1008/blog-peachtart-nuxt/git/trees/main?recursive=1`)

var mdList = []
var categories = []

for (let folder of folderList.tree) {
    if (folder.path == 'md') {
        var postList = await $fetch(folder.url)

        for (let post of postList.tree) {
            if (post.path.includes('.md')) {
                mdList.push(`https://raw.githubusercontent.com/jyhyun1008/blog-peachtart-nuxt/main/md/${post.path}`)
                categories.push(post.path.split('-')[1])
            }
        }
    }
}

var categorieset = new Set(categories);
categories = [...categorieset];

</script>