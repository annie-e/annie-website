<script setup>
import { defineProps } from 'vue';

const { project } = defineProps(['project']);

const { VITE_BASE_PHOTO_URL } = import.meta.env;;

const openUrl = (btnType) => {
    if (btnType === 'demo') {
        window.open(project.demoUrl, '_blank')
    } else {
        window.open(project.repoUrl, '_blank')
    }
}

</script>

<template>
    <div class="card-container">
        <div class="project-desc">
            <div class="project-info">
                <p>{{ project.description }}</p>
                <div class="project-tech">
                    <h5>Technology</h5>
                    <p>{{ project.tech }}</p>
                </div>
                <div class="project-btn">
                    <a-button class="btn" type="primary" @click="openUrl('demo')">
                        Demo
                    </a-button>
                    <a-button class="btn" type="primary" ghost @click="openUrl('repo')">
                        Repo
                    </a-button>
                </div>
            </div>
            <div class="project-img">
                <img :src="`${VITE_BASE_PHOTO_URL}${project.image}`" alt="project_img" />
            </div>
        </div>
    </div>
</template>

<style scoped>
h5 {
    color: var(--dark-blue);
}

.card-container {
    margin: 10px;
}

.project-desc {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.project-info {
    width: 50%;
}

.project-btn {
    display: flex;
    justify-content: start;
    align-items: center;
    margin-top: 20px;
}

.btn {
    margin-right: 10px;
    padding: 0px 50px;
}

img {
    width: 27em;
    height: 16em;
    border-radius: 3px;
    border: 5px solid white;
}

@media screen and (max-width: 600px) {
    img {
        width: calc(21em - 18vw);
        height: calc(13em - 10vw);
        margin-top: 30px;
    }
    .project-info {
        width: 100%;
    }
    .project-btn{
        justify-content: center;
    }
    .btn {
        height: 30px;
        padding: 4px 30px;
    }
    .project-desc{
        flex-direction: column;
    }
}
</style>