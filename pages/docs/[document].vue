<template>
    <div id="container-right">
        <h1 id="title"><a href="/">피치타르트 블로그</a></h1>
        <h2 id="category-title">
            <a href="/docs/">문서</a>
            <span v-for="tree of route.params.document.split('/')"> / <a :href="`/docs/${encodeURIComponent(route.params.document.split(tree)[0]+tree)}`">{{ tree }}</a></span>
        </h2>
        <div id="leftsidebar">
            <div style="margin-top: 1em;">목 차</div>
            <div v-for="(title, i) of titlesArray">
                <div :class="`nav-heading-${title[0]}`">
                    <a :href="`#heading-${i}`" v-if="!title.includes('href')">{{ title.split('>')[1] }}</a>
                    <a :href="`#heading-${i}`" v-else>{{ title.split('>')[2].split('<')[0] }}</a>
                </div>
            </div>
        </div>
        <div class="box-cont">
            <div class="post-content" v-html=markedContent></div>
        </div>
    </div>
</template>
<script setup>

import { marked } from 'marked';
const route = useRoute()
var content
try {
    content = await $fetch(`https://raw.githubusercontent.com/jyhyun1008/blog-peachtart-nuxt/main/docs/${decodeURI(route.params.document)}.md`)
} catch(e) {
    content = await $fetch(`https://raw.githubusercontent.com/jyhyun1008/blog-peachtart-nuxt/main/docs/${decodeURI(route.params.document)}/index.md`)
}
let markedArray = marked.parse(content).split('<h')
let titlesArray = []
let markedContent = markedArray[0]
for (let i=1; i<markedArray.length; i++) {
    titlesArray.push(markedArray[i].split('</')[0])
    markedContent += `<h${markedArray[i][0]} id="heading-${i}"${markedArray[i].slice(1)}`
}
function replacer(match, p1, offset, string) {
  return '"/docs/'+p1.replace(/\//gm, '%2F')+'"';
}
markedContent = markedContent.replace(/\"\/docs\/([^\"].+)\"/gm, replacer)

useSeoMeta({
  title: () => route.params.document,
  ogTitle: () => route.params.document,
  description: content.slice(0, 100).replace(/\n\n/gm, ' ').replace(/\n/gm, ' '),
  ogDescription: content.slice(0, 100).replace(/\n\n/gm, ' ').replace(/\n/gm, ' '),
  ogImage: content.split('img src="')[1] ? content.split('img src="')[1].split('" ')[0] : '/logo.png',
})

</script>