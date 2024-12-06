<template>
    <div id="container">
        <h1 id="title">피치타르트 블로그</h1>
        <div style="display: flex;">
            <div v-for="category of categories">
                <a :href="`/${category}`">{{ category }}</a>
            </div>
        </div>
        <div v-for="(post, i) of mdList">
            <a :href="`/${post.split('-')[1]}/${post.split('-')[2]}`" class="post-list">
                <div class="box-cont">
                    <h2>{{post.split('-')[2]}}</h2>
                    {{ marked.parse(mdContent[i].split('<--->')[1]) }}
                </div>
            </a>
        </div>
    </div>
</template>
<script setup>

import { marked } from 'marked';
//const route = useRoute()
var folderList = await $fetch(`https://api.github.com/repos/jyhyun1008/blog-peachtart-nuxt/git/trees/main?recursive=1`)

var mdList = []
var mdContent = []
var categories = []

async function getPost() {
    
    for (let folder of folderList.tree) {
        if (folder.path == 'md') {
            var postList = await $fetch(folder.url)

            for (let post of postList.tree) {
                if (post.path.includes('.md')) {
                    mdList.push(post.path.split('.')[0])
                    categories.push(post.path.split('-')[1])

                    var content = await $fetch(`https://raw.githubusercontent.com/jyhyun1008/blog-peachtart-nuxt/main/md/${post.path}`)
                    mdContent.push(content)
                }
            }

            console.log(mdContent)
        }
    }

    var categorieset = new Set(categories);
    categories = [...categorieset];
}

await getPost()

</script>