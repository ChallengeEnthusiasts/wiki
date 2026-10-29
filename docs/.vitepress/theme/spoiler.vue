<script setup lang="ts">
import { ref } from 'vue'
const revealed = ref(false)
</script>

<template>
  <span
    class="spoiler"
    :class="{ revealed }"
    role="button"
    tabindex="0"
    :title="revealed ? '' : 'Click to reveal'"
    @click="revealed = true"
    @keydown.enter="revealed = true"
  ><slot /></span>
</template>

<style scoped>
.spoiler {
  background: var(--vp-c-text-1);
  color: transparent;
  border-radius: 3px;
  padding: 0 2px;
  cursor: pointer;
  transition: color 0.2s, background 0.2s;
}
.spoiler :deep(*) { color: transparent; }
.spoiler.revealed {
  background: var(--vp-c-default-soft);
  color: inherit;
  cursor: auto;
}
.spoiler.revealed :deep(*) { color: inherit; }
</style>
