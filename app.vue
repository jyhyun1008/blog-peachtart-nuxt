<template>
  <div id="app">
    <Head>
      <Title>CabinetKey 캐비닛키</Title>
      <Meta name="description" content="피치타르트 공식 블로긔"/>
      <link rel="stylesheet" href="https://cdn.hugeicons.com/font/hgi-stroke-rounded.css">
    </Head>
    <NuxtLayout>
      <div id="top-menu">
        <div class="logo-menu">
          <div class="logo-item"><a href="https://peacht.art"><img src="https://tistory1.daumcdn.net/tistory/7128980/skinSetting/e2f6d4b6e4b8408fa690e1a600090236"></a></div>
        </div>
        <div class="mid-menu">
          <div class="menu-item"><a href="https://blog.peacht.art"><i class="hgi-stroke hgi-pencil"></i><span class="fullname"> 블로그</span></a></div>
          <div class="menu-item"><a href="https://d.peacht.art"><i class="hgi-stroke hgi-comment-01"></i><span class="fullname"> 커뮤니티</span></a></div>
          <div class="menu-item"><a href="https://blog.peacht.art/pages/docs"><i class="hgi-stroke hgi-doc-01"></i><span class="fullname"> 문서</span></a></div>
          <div class="menu-item"><a href="https://blog.peacht.art/pages/shop"><i class="hgi-stroke hgi-shopping-bag-02"></i><span class="fullname"> 쇼핑</span></a></div>
        </div>
      </div>
      <NuxtPage />
    </NuxtLayout>
  </div>
</template>

<script>


export default {
    mounted() {
    }
  }
</script>
<style>

/*basic settings*/

@import url('https://fastly.jsdelivr.net/npm/galmuri@latest/dist/galmuri.css');

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

:root {
  --accent: #ff9899;
  --accent-light: #ffddcc;
  --fg: #262629;
  --border: #d7d7de;
  --bg: #f8f8fb;
}

div {
  box-sizing: border-box;
}

a {
  color: var(--accent);
  text-decoration: none;
}

a.post-list {
  color: inherit !important;
  width: 100%;
}

body {
  font-family: Galmuri11;
  background-color: var(--bg);
  color: var(--fg);
  overscroll-behavior-x: none;
  font-size: 14px;
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
    background: #ff9899;
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
}

.mid-menu {
    height: 3em;
    display: flex;
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

</style>