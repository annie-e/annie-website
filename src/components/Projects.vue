<script setup>
import Container from "./Container.vue";
import { onMounted, ref } from "vue";
import { supabase } from '../supabase'
import ProjectCard from "./ProjectCard.vue";

const projectList = ref([]);
const activeKey = ref();

onMounted(async()=>{
    fetchProject();
    changeFontSizeOfTab();
})

const changeFontSizeOfTab = () =>{
    setTimeout(()=>{
        document.querySelectorAll(".ant-tabs-nav .ant-tabs-tab").forEach(t => {
            t.style.fontSize='17px';
        })
    }, 300);
}

const fetchProject = async()=> {
    const { data } = await supabase.from("projects").select();
    data.forEach((p) => {
        projectList.value.push({
            name: p.name,
            description: p.description,
            demoUrl: p.demo_url,
            repoUrl: p.repo_url,
            image: p.image,
            tech: p.technologies
        })
    });
}

</script>

<template>
    <Container>
        <div class="project-container">
            <a-divider class="component-header">Projects</a-divider>
            <div class="project-tabs">
                <a-tabs v-model:activeKey="activeKey">
                    <a-tab-pane v-for="(project, index) in projectList" :key="index" :tab="project.name">
                        <ProjectCard :project="project" />
                    </a-tab-pane>
                </a-tabs>
            </div>
        </div>
    </Container>
</template>

<style scoped>
.project-tabs {
    margin: 0 60px;
    padding: 0px 0px 40px;
}
</style>