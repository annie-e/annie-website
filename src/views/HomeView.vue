<script setup>
import Intro from "../components/Intro.vue"
import About from "../components/About.vue"
import Projects from "../components/Projects.vue"
import Contact from "@/components/Contact.vue";

</script>

<template>
  <main>
    <a-layout class="layout">
      <Intro />
      <div id="about">
        <About />
      </div>
      <div id="projects">
        <Projects />
      </div>
      <div id="contact">
        <Contact />
      </div>
    </a-layout>
  </main>
</template>
