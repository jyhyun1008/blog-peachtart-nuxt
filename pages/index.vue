<template>
    <div id="container">
        <h1 id="title">피치타르트 블로그</h1>
        <div style="display: flex; align-items: center; gap: 12px">
            카테고리 : 
            <div v-for="category of categories" class="category-list">
                <a :href="`/p/${category}`">{{ category }}</a>
            </div>
        </div>
        <div v-for="(post, i) of mdList">
            <a :href="`/p/${post.split('-')[0]}/${post.split('-')[1]}-${post.split('-')[2]}`" class="post-list">
                <div class="box-cont" v-if="mdContent[i].split('<--->')[0].split('title:')[1]">
                    <div class="post-cont">
                        <h2>{{ mdContent[i].split('<--->')[0].split('title:')[1].split('\n')[0] }}</h2>
                        <p>{{ mdContent[i].split('<--->')[1].slice(0,256) }}</p>
                    </div>
                    <div v-if="mdContent[i].split('<--->')[0].split('eyeCatchImg:').length > 1">
                        <img :src="`${mdContent[i].split('eyeCatchImg:')[1].split('\n')[0]}`" />
                    </div>
                </div>
            </a>
        </div>
    </div>
</template>
<script setup>

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
                    categories.push(post.path.split('-')[0])

                    var content = await $fetch(`https://raw.githubusercontent.com/jyhyun1008/blog-peachtart-nuxt/main/md/${post.path}`)
                    mdContent.push(content)
                }
            }
        }
    }

    var categorieset = new Set(categories);
    categories = [...categorieset];
}

await getPost()

</script>