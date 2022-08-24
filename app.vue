<template>
  <div>
    <Header />
    <NuxtPage />
    <Footer />
  </div>
</template>

<script setup>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
</script>

<style>
:root{
    --orange: #FFA51F;
    --dark-orange: #b86f02;
    --pastel: #FFD79C;
    --dark: #404040;
    --light: #fff;
    --grey: #646464;
    --lightgrey: #eeeeee;
    --text-color: #000;
}

html {
    scroll-behavior: smooth;
}

* {
    font-family: 'Poppins', sans-serif;
    text-decoration: none;
    color: unset;
    list-style: none;
}

html, body, p, ul, h3 {
    margin: 0;
    padding: 0;
}

body {
    position: relative;
    min-height: 100vh;
}

main {
    max-width: 800px;
    margin: 100px auto auto;
    min-height: calc(100vh - 6rem);
}

/** media query for mobile */
@media screen and (max-width: 768px) {
    body {
        width: 100%;
        max-width: 100%;
    }
    main {
        width: 100%;
        max-width: 100%;
        margin: 150px 0 0;
    }
}

.bg-orange {
    background-color: var(--orange);
}

.text-orange {
    color: var(--orange);
}

.hover-orange:hover {
    color: var(--orange);
    border-color: var(--orange);
}

.text-pastel {
    color: var(--pastel);
}
</style>