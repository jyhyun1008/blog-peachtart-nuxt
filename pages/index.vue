<template>
    <div id="container">
        <h1 id="title"><a href="/">호토라즈의 블로그</a></h1>
        <div style="display: flex; align-items: center; gap: 12px">
            카테고리 :
            <div v-for="category of categories" class="category-list">
                <a :href="`/p/${category}`">{{ category }}</a>
            </div>
        </div>
        <div v-for="(post, i) in mdList">
            <a :href="`/p/${post.split('-')[2].split('.')[0]}/${post.split('-')[0]}-${post.split('-')[1]}`"
                class="post-list">
                <div class="box-cont" v-if="mdContent[i].split('<--->')[0].split('title:')[1]">
                    <div class="post-cont">
                        <h2>{{ mdContent[i].split('<--->')[0].split('title:')[1].split('\n')[0].slice(0, 30) }}</h2>
                        <p>{{ mdContent[i].split('<--->')[1].slice(0, 100) }}...</p>
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
const repoUri = 'HotoRas/blog'
const blogContentPath = 'blog/md'
var folderList = await $fetch(`https://api.github.com/repos/${repoUri}/git/trees/main?recursive=1`)

let mdList = []
let mdContent = []
let categories = []

async function getPost() {
    let postList = {}
    folderList.tree.foreach(async (folder) => {
        if (folder.path == blogContentPath) {
            postList = await $fetch(folder.url)
        }
    })
    postList.tree.foreach(async (post) => {
        if (post.path.includes('.md')) {
            mdList.push(post.path.split('.')[0])
            let cat = post.path.split('-')[2] ? post.path.split('-')[2].split('.')[0] : '미분류'
            categories.push(cat)

            let content = await $fetch(`https://raw.githubusercontent.com/${repoUri}/main/${blogContentPath}/${post.path}`)
            mdContent.push(content)
        }
    })

    mdList.reverse()
    mdContent.reverse()

    let categorieset = new Set(categories);
    categories = [...categorieset];
}

await getPost()

</script>