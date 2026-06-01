<script setup lang="ts">
const { data: posts } = await useAsyncData('blog-posts', () => {
  return queryCollection('content').where('path', 'LIKE', '/blog/%').all()
})
</script>

<template>
  <main>
    <h1>Blog</h1>
    <ul>
      <li v-for="post in posts" :key="post.path">
        <NuxtLink :to="post.path">{{ post.title }}</NuxtLink>
      </li>
    </ul>
  </main>
</template>
