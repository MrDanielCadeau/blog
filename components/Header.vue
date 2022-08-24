<template>
    <header>
        <a href="#" class="active-link"><h1>blog.<span class="text-orange">d</span>cadeau<span class="text-orange">.</span>tech</h1></a>
        <nav>
            <a href="https://www.dcadeau.tech" class="not-active-link">About me</a>
            <a href="https://www.linkedin.com/in/daniel-cadeau-dev/" class="not-active-link">LinkedIn</a>
            <a href="https://github.com/MrDanielCadeau" class="not-active-link">Github</a>
        </nav>
    </header>
</template>

<script setup>
</script>

<style scoped>
header {
    position: fixed;
    z-index: 1;
    top: 0;
    left: 0;
    background-color: var(--light);
    width: 100%;
    height: 5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px solid var(--lightgrey);
}

header > a {
    padding: 0 64px;
}

header nav {
    padding: 0 64px;
}

header nav a {
    font-size: large;
    width: fit-content;
    position: relative;
}

header nav a:after {
    content: '';
    position: absolute;
    width: 100%;
    transform: scaleX(0);
    height: 2px;
    bottom: -2px;
    left: 0;
    background-color: var(--orange);
    transform-origin: bottom right;
    transition: transform 0.25s ease-out;
}

header nav a:hover:after {
    transform: scaleX(1);
    transform-origin: bottom left;
}

header nav a:not(:last-child) {
    margin-right: 16px;
}
</style>