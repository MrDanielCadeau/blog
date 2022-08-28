<template>
  <main>
    <ContentDoc v-slot="{ doc }">
      <h1>{{ doc.title }}</h1>
      <ContentRenderer :value="doc" />
    </ContentDoc>
    <h2>Last articles</h2>
    <ul>
       <ContentList path="/" v-slot="{ list }">
        <li>
          <a v-for="article in list" :key="article._path" :href="article._path">
            <h2>{{ article.title }}</h2>
            <p>{{ article.description }}</p>
          </a>
        </li>
      </ContentList>
    </ul>
  </main>
</template>
