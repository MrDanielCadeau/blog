<template>
    <footer id="footer">
        <section>
            <div>
                <p class="text-bold text-light">Feel free to contact me</p>
                <a href="mailto:contact@dcadeau.tech" class="text-pastel">contact@dcadeau.tech</a>
            </div>
            <p class="text-bold text-light"><span class="text-pastel">d</span>cadeau<span class="text-pastel">.</span>tech 2022</p>
        </section>
    </footer>
</template>

<script setup>
</script>

<style scoped>
footer {
    width: 100%;
    padding: 64px 0;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: var(--dark);
    height: 6rem;
}

footer > section {
    padding: 0 64px;
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

footer section div {
    line-height: 2rem;
}

footer section div,
footer section > p {
    padding: 0;
}

/** mobile query */
@media screen and (max-width: 768px) {
    footer {
        flex-direction: column;
        font-size: smaller;
    }
    footer section {
        width: 100%;
        flex-direction: column;
        padding: 0;
    }
    footer section div,
    footer section > p {
        padding: 0 64px;
    }
    footer section:last-child {
        margin-top: 32px;
    }
    footer * {
        text-align: left!important;
    }
}
</style>