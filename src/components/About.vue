<script setup>
import Container from "./Container.vue"
import { LinkedinOutlined, GithubOutlined, InstagramOutlined } from '@ant-design/icons-vue';
</script>

<template>
    <Container>
        <div class="about-container">
            <a-divider class="component-header">About</a-divider>
            <div class="me-container">
                <div class="description">
                    <p> My name is <strong style='color:var(--blue)'>E Hyun Kim</strong> and my preferred name is <b
                            style='color:var(--blue)'>Annie</b>.
                        I am a self-motivated and creative individual currently working as a
                        <strong style='color:var(--blue)'>Full Stack Java developer</strong>
                        in Toronto, Ontario.
                    </p>
                    <p>
                        I have a unique background in nursing where my interest in coding sparked and
                        have graduated from the Software Engineering at Sheridan College to start my journey as a
                        developer.

                        Through this experience, I have gained a solid knowledge and practical foundation of
                        Object Oriented Programming and hold strong communication and collaboration skills.

                        I continously strive to learn the newest technologies and Vue.js is next on the list!
                    </p>
                </div>
                <div class="linkedin">
                    <a-card style="width: 220px">
                        <template #cover>
                            <img alt="programmer_img" src="../assets/programmer.png" />
                        </template>
                        <a-card-meta>
                            <template #description>
                                <div class="links">
                                    <a href="https://www.linkedin.com/in/annie-kim-sd/" target="_blank">
                                        <LinkedinOutlined />
                                    </a>
                                    <a href="https://github.com/annie-e" target="_blank">
                                        <GithubOutlined />
                                    </a>
                                    <a href="https://www.instagram.com/colour_ey/" target="_blank">
                                        <InstagramOutlined />
                                    </a>
                                </div>
                            </template>
                        </a-card-meta>
                    </a-card>
                </div>
            </div>
        </div>
    </Container>
</template>

<style scoped>
.me-container {
    display: flex;
    justify-content: space-around;
    align-items: center;
    padding: 40px 0px;
}

.description {
    width: 50%;
    line-height: 30px;
}

.links {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 25px;
}

img {
    padding: 15px;
}
</style>