<script setup>
import { ProjectOutlined, UserOutlined, ContactsOutlined } from '@ant-design/icons-vue';
import Container from "./Container.vue"
import { h, ref } from "vue";

const items = ref([
  {
    key: 'about',
    icon: () => h(UserOutlined),
    label: h('a', { href: '#about' }, 'About'),
    title: 'About',
  },
  {
    key: 'projects',
    icon: () => h(ProjectOutlined),
    label: h('a', { href: '#projects' }, 'Projects'),
    title: 'Projects',
  },
  {
    key: 'contact',
    icon: () => h(ContactsOutlined),
    label: h('a', { href: '#contact' }, 'Contact'),
    title: 'Contact',
  },
])

</script>

<template>
  <Container>
    <a-menu mode="horizontal" class="menu-container" :items="items" />
  </Container>
</template>

<style scoped>
.menu-container {
  padding-top: 1vh;
  font-size: 16px;
}

.icon {
  display: inline;
  margin: 5px;
  font-size: 16px;
}
</style>