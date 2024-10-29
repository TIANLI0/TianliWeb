<script setup>
import { defineProps } from "vue";

const props = defineProps({
  links: Array,
});
</script>

<template>
  <section class="links-section">
    <h2 class="section-title">Links</h2>
    <div class="links">
      <a
        :href="link.url"
        class="link-card"
        v-for="link in links"
        :key="link.url"
      >
        <div class="link-item">
          <img :src="link.icon" alt="icon" class="link-icon" />
          <span class="link-name">{{ link.name }}</span>
        </div>
      </a>
    </div>
  </section>
</template>

<style scoped>
.links-section {
  background-color: rgb(var(--mdui-color-inverse-primary));
  padding: 40px 30px;
  border-top-left-radius: 40px;
  border-top-right-radius: 40px;
}

.section-title {
  font-size: 18px;
  font-weight: bold;
  text-transform: uppercase;
}

.links {
  display: grid;
  gap: 20px;
  grid-template-columns: repeat(3, 1fr);
}

.link-card {
  background-color: rgb(var(--mdui-color-primary-container));
  border-radius: 30px;
  padding: 20px 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  gap: 30px;
  text-decoration: none;
}

.link-item {
  display: flex;
  align-items: center;
  gap: 15px;
}

.link-icon {
  width: 40px;
}

.link-name {
  font-size: 18px;
  font-weight: bold;
  color: black;
}

@media (prefers-color-scheme: dark) {
  .link-name {
    color: rgb(255, 255, 255);
  }
  .link-icon {
    filter: invert(1);
  }
}

@media (max-width: 768px) {
  .links {
    grid-template-columns: 1fr;
  }
}
</style>
