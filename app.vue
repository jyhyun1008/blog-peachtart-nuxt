<template>
  <div id="app">
    <Head>
      <Title>피치타르트 블로그</Title>
      <Meta name="description" content="피치타르트 공식 블로그"/>
      <link rel="stylesheet" href="https://cdn.hugeicons.com/font/hgi-stroke-rounded.css">
      <meta property="og:title" content="피치타르트 블로그" /> 
      <meta property="og:description" content="피치타르트 공식 블로그" /> 
      <meta property="og:image" content="/logo.png" /> 
    </Head>
    <NuxtLayout>
      <div id="top-menu">
        <div class="logo-menu">
          <div class="logo-item"><a href="https://peacht.art"><img src="/logo.png"></a></div>
        </div>
        <div class="mid-menu">
          <div class="menu-item"><a href="https://blog.peacht.art"><i class="hgi-stroke hgi-pencil"></i><span class="fullname"> 블로그</span></a></div>
          <div class="menu-item"><a href="https://blog.peacht.art/g"><i class="hgi-stroke hgi-image-02"></i><span class="fullname"> 갤러리</span></a></div>
          <div class="menu-item"><a href="https://d.peacht.art"><i class="hgi-stroke hgi-comment-01"></i><span class="fullname"> 커뮤니티</span></a></div>
          <div class="menu-item"><a href="https://blog.peacht.art/docs"><i class="hgi-stroke hgi-doc-01"></i><span class="fullname"> 문서</span></a></div>
          <div class="menu-item"><a href="https://blog.peacht.art/shop"><i class="hgi-stroke hgi-shopping-bag-02"></i><span class="fullname"> 쇼핑</span></a></div>
        </div>
      </div>
      <NuxtPage />
    </NuxtLayout>
  </div>
</template>
<script>
</script>
<style>

/*basic settings*/

@import url('https://fastly.jsdelivr.net/npm/galmuri@latest/dist/galmuri.css');

@font-face {
     font-family: 'DungGeunMo';
     src: url('https://fastly.jsdelivr.net/gh/projectnoonnu/noonfonts_six@1.2/DungGeunMo.woff') format('woff');
     font-weight: normal;
     font-style: normal;
}

@font-face {
    font-family: 'Pretendard';
    src: url('https://fastly.jsdelivr.net/gh/Project-Noonnu/noonfonts_2107@1.1/Pretendard-Regular.woff') format('woff');
    font-weight: 400;
    font-style: normal;
}

@font-face {
    font-family: 'Pretendard';
    src: url('https://fastly.jsdelivr.net/gh/Project-Noonnu/noonfonts_2107@1.1/Pretendard-Bold.woff') format('woff');
    font-weight: 700;
    font-style: normal;
}

/*프리텐다드 쓸거면 이거 해제하세요*/

/* body {
  font-family: 'Pretendard' !important;
}

.box-cont, .box-cont-grid {
  font-size: 16px;
}

#title, h1, h2 {
  font-family: unset !important;
} */

/* basic */

:root {
  --accent: #ff9899;
  --accent-light: #ffddcc;
  --fg: #262629;
  --border: #d7d7de;
  --bg: #f8f8fb;
}

#nuxt-devtools-container {
  display: none;
}

div {
  box-sizing: border-box;
}

a {
  color: var(--accent);
  text-decoration: none;
}

body {
  /*font-family: 'Pretendard';*/
  font-family: Galmuri11;
  background-color: var(--bg);
  color: var(--fg);
  overscroll-behavior-x: none;
  font-size: 14px;
  line-height: 1.6;
  margin: 0;
  padding: 0;
}

#title, h1, h2 {
  font-family: 'DungGeunMo';
}

.post-content > h1, .post-content > h2 {
  font-family: 'DungGeunMo';
  border-bottom: 1px solid var(--border);
  padding-bottom: 0.2rem;
}

img {
  max-width: 100%;
  border-radius: 10px;
}

blockquote {
  border-left: 3px solid var(--accent);
  margin-inline-start: 0;
  margin-inline-end: 0;
  padding: 0.5em 0 0.5em 1em;
}

code, pre, blockquote {
  background-color: var(--bg);
}

pre {
  overflow-x: scroll;
}

code, pre {
  padding: 0 4px;
  border-radius: 10px;
}

/*navbar*/

.menu_toolbar {
    display: none;
}

#top-menu {
    box-sizing: border-box;
    width: 100vw;
    height: 3em;
    display: flex;
    background: var(--accent);
    position: fixed;
    z-index: 9999999;
    top:0;
    left: 0;
    padding: 0 1em;
    color: #fff;
    align-items: center;
    justify-content: space-between;
    overflow: hidden;
    box-shadow: 5px 5px 5px #00000011;
}

#top-menu img {
    height: 3em;
    width: 3em;
}

.mid-menu {
    height: 3em;
    display: flex;
}

.logo-item {
  height: 3em;
}

.logo-item:hover {
    opacity: 0.6;
}

.menu-item {
    height: 3em;
    padding: 0.25em 1em;
}

.menu-item > a {
    color: #fff;
    display: flex;
    gap: 5px;
    align-items: center;
    height: 2.5em;
}

.menu-item i{
    font-size: 1.5em;
}

.menu-item .fullname {
	display: none;
}

.menu-item:hover {
    background: #ffddcc;
}

.menu-item:hover .fullname {
	display: inline;
}

#container {
  width: calc(100vw - 20px);
  max-width: 640px;
  margin: 100px auto 100px auto;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.box-cont {
    width: 100%;
    border-radius: 15px;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
    background-color: white;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    gap: 10px;
    padding: 10px;
}

.box-cont-grid {
    width: 100%;
    border-radius: 15px;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
    background-color: white;
    overflow: hidden;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
    padding: 10px;
}

.box-cont-grid img {
    width: 100% !important;
    max-width: unset !important;
    aspect-ratio: 1 / 1 !important;
    object-fit: cover;
    object-position: center;
}

/*categorylist*/

.category-list {
  border-radius: 10px;
  background-color: var(--accent);
  padding: 0 4px;
  font-size: 16px;
}

.category-list a {
  color: #fff !important;
}

/*postlist*/

a.post-list {
  color: inherit !important;
  width: 100%;
  display: flex;
}

.post-list img {
  max-width: 200px;
  width: 40vw;
  height: 100%;
  object-fit: cover;
  object-position: center;
  border-radius: 10px;
}

.post-list .box-cont {
  flex-direction: row !important;
  justify-content: space-between;
}

/*post*/

#post-header {
  display: flex;
  flex-direction: column;
  align-items: center;
}

/*docs*/

#container-right {
  position:relative;
  left: 100px;
  width: calc(100vw - 200px);
  max-width: 640px;
  margin: 100px auto;
  display: flex;
  flex-direction: column;
  gap: 20px;
}

#leftsidebar {
  position: fixed;
  width: 200px;
  z-index: 999;
  height: 100dvh;
  top: 0;
  left: 0;
  background-color: white;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
  overflow-x: hidden;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
  padding: 4em 1em 1em 1em;
  gap: 10px;
}

#leftsidebar a {
  color: inherit !important;
}

@media (max-width: 900px) {
  #leftsidebar {
    display: none;
  }

  #container-right {
    position: unset;
    width: 100vw;
    max-width: 640px;
    margin: 100px auto;
    display: flex;
    flex-direction: column;
    gap: 20px;
  }

}

.nav-heading-1 {
  font-weight: 700;
  margin-top: 1em;
}

.nav-heading-2 {
  padding-left: 1em;
}

.nav-heading-3 {
  padding-left: 2em;
}

.nav-heading-4 {
  padding-left: 3em;
}

.nav-heading-5 {
  padding-left: 4em;
}

.nav-heading-6 {
  padding-left: 5em;
}

</style>