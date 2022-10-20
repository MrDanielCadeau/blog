<template>
  <main>
    <article v-if="data">
      <img id="preview" :src="'/img' + data.preview" :alt="data.alt" class="article-image" />
      <p class="date">{{ new Date(data.date).toISOString().slice(0, 10) }}</p>
      <div class="title">
        <h1>{{ data.title }}</h1>
        <div></div>
      </div>
      <ContentRenderer :value="data" />
    </article>
    <section v-else>
      <h2>404 - Article not found</h2>
      <a href="/">Go back to home</a>
    </section>
    <div class="separator">
      <h2>Latest articles</h2>
      <div></div>
      <div></div>
      <div></div>
    </div>
    <ul>
      <ContentList :query="query" v-slot="{ list }">
        <li class="last_article" v-for="article in list">
          <a :key="article._path"
          :href="article._path">
          <h2>{{ article.title }}</h2>
          <p>{{ article.description }}</p>
        </a>
      </li>
    </ContentList>
  </ul>
</main>
</template>

<script setup lang="ts">
import type { QueryBuilderParams } from '@nuxt/content/dist/runtime/types'

const { path } = useRoute()

const { data } = await useAsyncData(`content-${path}`, () => {
  return queryContent().where({ _path: (path === '/')
  ? '/2022-10-18-welcome-to-dcadeau-tech-blog'
  : path }).findOne()
})

const query: QueryBuilderParams = {
  limit: 5, sort: [{ date: -1 }],
  first: false,
  skip: 0,
  only: [],
  without: [],
  where: [],
  surround: {
    query: '',
    before: 0,
    after: 0
  }
}
</script>

<style>
div.title {
  position: relative;
  height: 100%;
  width: fit-content;
}

div.title h1 {
  width: fit-content;
}

div.title div {
  padding: 0 4px;
  z-index: -1;
  position: absolute;
  bottom: 6px;
  left: 0;
  background-color: var(--pastel);
  width: fit-content;
  height: 12px;
  width: 100%;
  border-top-right-radius: 16px;
  border-bottom-right-radius: 16px;
}

article > *:not(img) {
  padding: 0 16px;
}

p.date {
  font-size: small;
  color: var(--dark-orange);
  
}

ul li.last_article {
  margin: 16px 0;
  padding: 0 16px;
}

ul li.last_article:hover a {
  opacity: 0.8;
}

ul li.last_article a h2 {
  margin: 4px 0;
  font-size: 1.5rem;
}

p {
  line-height: 1.75em;
}

div > h2 {
  margin: 8px 0;
}

.separator {
  padding: 16px 16px;
  margin: 16px 0;
  text-align: right;
}

.separator h2 {
  color: var(--dark-orange);
}

.separator div {
  height: 1px;
  width: 100%;
  background-color: var(--dark-orange);
  margin: 4px 0;
}

#preview {
  width: 100%;
  max-height: 250px;
  object-fit: cover;
  margin-bottom: 32px;
}
</style>