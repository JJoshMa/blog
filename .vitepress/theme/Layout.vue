<script setup lang="ts">
import { useData } from 'vitepress'

const { site, frontmatter } = useData()
</script>

<template>
  <img src="../../assets/DragonMedium.png"  style="position: fixed;top: 0;left: 42px;  width: 60px;height: 60px" alt="404"/>
  <div v-if="frontmatter.home">
    <h1>{{ site.title }}</h1>
    <p>{{ site.description }}</p>
    <ul>
      <li><a href="/markdown-examples">Markdown Examples</a></li>
      <li><a href="/api-examples">API Examples</a></li>
    </ul>
  </div>
  <div v-else>
    <a href="/">Home</a>
    <Content />
  </div>
</template>
