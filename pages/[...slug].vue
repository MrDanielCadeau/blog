<template>
  <main>
    <ContentDoc v-slot="{ doc }">
      <img id="preview" :src="`static${doc.preview}`" alt="image" />
      <p class="date">{{ new Date(doc.date).toISOString().slice(0, 10) }}</p>
      <div class="title">
        <h1>{{ doc.title }}</h1>
        <div></div>
      </div>
      <ContentRenderer :value="doc" />
    </ContentDoc>
    <h2 class="separator">Last articles</h2>
    <ul>
       <ContentList path="/" v-slot="{ list }">
        <li class="last_article" v-for="article in list.reverse().slice(0, 5)">
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
  bottom: 8px;
  left: 0;
  background-color: var(--pastel);
  width: fit-content;
  height: 12px;
  width: 100%;
  border-top-right-radius: 16px;
  border-bottom-right-radius: 16px;
}

p.date {
  font-size: small;
  color: var(--dark-orange);

}

ul li.last_article {
  margin: 16px 0;
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

#preview {
  width: 100%;
  max-height: 250px;
  object-fit: cover;
  margin-bottom: 32px;
}

.separator {
  color: var(--dark-orange);
  margin: 16px 0;
  padding: 16px 0;
  border-bottom: 1px solid var(--dark-orange);;
}
</style>