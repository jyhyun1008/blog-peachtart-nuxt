<template>
    <div id="container">
        <h1 id="title"><a href="/">피치타르트 블로그</a></h1>
        <div class="box-cont">
            <div id="post-header">
                <h2>{{ route.params.post }}</h2>
                <div><a :href="`/p/${route.params.category}`">{{ decodeURI(route.params.category) }}</a></div>
                <div style="font-size: 0.8em;">{{ route.params.post.split('-')[0] }}</div>
            </div>
            <div><img :src="`/p/${content}`" /></div>
        </div>
    </div>
</template>
<script setup>

import { marked } from 'marked';
const route = useRoute()
var content
try {
    content = await $fetch(`https://raw.githubusercontent.com/jyhyun1008/blog-peachtart-nuxt/main/md/${route.params.post}-${route.params.category}.jpg`)
} catch(e) {
    try {
        content = await $fetch(`https://raw.githubusercontent.com/jyhyun1008/blog-peachtart-nuxt/main/md/${route.params.post}-${route.params.category}.png`)
    } catch(e1) {
        content = await $fetch(`https://raw.githubusercontent.com/jyhyun1008/blog-peachtart-nuxt/main/md/${route.params.post}-${route.params.category}.webp`)
    }
}
var postTitle = content.split('<--->')[0]?.split('title:')[1]?.split('\n')[0]

</script>