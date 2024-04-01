<script setup>
import Container from "./Container.vue"

</script>

<template>
    <Container>
        <div class="intro-container">
            <div class="info-container">
                <h1 class="name">Hello, I am Annie</h1>
                <h2 class="role">Full Stack Developer</h2>
                <h5 class="description">dedicated to continuous learning and committed to taking initiatives for
                    professional development</h5>
            </div>
        </div>
    </Container>
</template>

<style scoped>
h5 {
    color: var(--dark-grey);
}

.intro-container {
    width: 100%;
    height: 50vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

.info-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    align-items: center;
    text-align: center;
}

.name {
    margin: 0;
}

.description {
    text-align: center;
}

@media screen and (max-width: 600px) {
    .name {
        font-size: calc(4em + 0.9vw);
        line-height: 70px;
    }

    .role {
        font-size: calc(1.5em + 0.5vw);
        margin-top: 10px;
    }

}
</style>