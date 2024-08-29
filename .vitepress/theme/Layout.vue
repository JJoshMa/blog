<script setup lang="ts">
import {Content, useData} from 'vitepress'

const data = useData()
const {site, frontmatter} = data
console.log(data.localeIndex.value)
</script>

<template>
  <img src="../../assets/DragonMedium.png" class="dragon-image" alt="404"/>
  <div >
    <a href="/">Home</a>
    <h1>{{ site.title }}</h1>
    <a href="/compiler/编译原理">测试</a>
    <a href="/api-examples">引用 </a>
    
    <div>{{frontmatter}}</div>
    <div>{{data}}</div>
    
    <div style="padding-left: 24px;max-width: 90%" >
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