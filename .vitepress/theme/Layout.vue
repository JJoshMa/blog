<script setup lang="ts">
import {Content, useData} from 'vitepress'
import {ref} from "vue";

const data = useData()
const {site} = data

const navList = ref(['root'])

document.addEventListener('click', (e) => {
  const fn = (i: number) => {
    if (i === 0)
      return;

    const currentTitle = data.page.value.title
    if (currentTitle === '') {
      setTimeout(() => fn(--i), 50)
      return;
    }
    if (navList.value[navList.value.length - 1] === currentTitle) {
      return
    }

    for (let i = 0; i < navList.value.length; i++) {
      if (currentTitle === navList.value[i]) {
        navList.value = navList.value.splice(0, i + 1)
        return;
      }
    }

    navList.value.push(data.page.value.title)
  }

  setTimeout(() => fn(20), 50)
})

</script>

<template>
  <img src="../../assets/DragonMedium.png" class="dragon-image" alt="404"/>
  <div>
    <a href="/">Home</a>
    <h1>{{ site.title }}</h1>
    <a href="/compiler/编译原理">编译原理</a>

    <a href=""> 123 </a>

    <a href="/api-examples">examples </a>
    <div>{{ navList }}</div>

    <div style="padding-left: 24px;max-width: 90%">
      <Content/>
    </div>
  </div>
</template>

<style scoped>

.dragon-image {
  position: fixed;
  bottom: 12px;
  right: 12px;
  width: 60px;
  height: 60px;
  z-index: 1000;
}

a:visited {
  color: #0000FF;
}

</style>
