<script setup lang="ts">
import { useData } from 'vitepress'
import DefaultTheme from 'vitepress/theme'
import { provide } from 'vue'

const { isDark } = useData()

provide('toggle-appearance', () => {
  isDark.value = !isDark.value
})
</script>

<template>
  <DefaultTheme.Layout>
    <template #layout-top>
      <div class="banner">
        This project has been moved to
        <a href="https://yomihon.github.io/">yomihon.github.io</a>.
      </div>
    </template>
  </DefaultTheme.Layout>
</template>


<style>
:root {
  --banner-height: 44px; /* 1.5rem (24px) + 10px padding * 2 = 44px approx, adjusting to match */
}

.banner {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  height: var(--banner-height);
  background-color: var(--vp-c-warning-soft);
  color: var(--vp-c-warning-1);
  padding: 10px;
  text-align: center;
  font-weight: bold;
  box-sizing: border-box;
  line-height: normal;
}

.banner a {
  text-decoration: underline;
}

/* Adjust layout to accommodate banner */
.VPNav {
  top: var(--banner-height) !important;
}

.VPSidebar {
  top: calc(var(--vp-nav-height) + var(--banner-height)) !important;
}

.VPLocalNav {
  top: var(--banner-height) !important;
}

/* Push content down */
.Layout {
  padding-top: var(--banner-height);
  min-height: 100vh;
}
</style>
