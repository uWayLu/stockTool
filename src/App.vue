<template>
  <Portal />
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import HelloWorld from './components/HelloWorld.vue'
import Portal from './components/Portal.vue'

export default defineComponent({
  name: 'App',
  components: {
    HelloWorld,
    Portal
  }
})
</script>

<style>
@import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.4.1/font/bootstrap-icons.css");
</style>