<script setup>
import { defineProps } from "vue";

const props = defineProps({
  projects: Array,
});
</script>

<template>
  <section class="program-section">
    <h2 class="section-title">Projects</h2>
    <div class="projects">
      <div class="project-card" v-for="project in projects" :key="project.name">
        <a
          :href="project.url"
          class="project-item"
          target="_blank"
          rel="noopener noreferrer"
        >
          <img
            :src="project.img"
            :alt="project.description"
            loading="lazy"
            class="project-img"
          />
          <div class="project-info">
            <span class="project-name">{{ project.name }}</span>
            <span class="project-description">{{ project.description }}</span>
          </div>
        </a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.program-section {
  background-color: rgb(var(--mdui-color-inverse-primary));
  padding: 40px 30px;
  border-bottom-left-radius: 40px;
  border-bottom-right-radius: 40px;
}

.section-title {
  font-size: 18px;
  font-weight: bold;
  text-transform: uppercase;
}

.projects {
  display: grid;
  gap: 20px;
  grid-template-columns: repeat(3, 1fr);
}

.project-card {
  background-color: rgb(var(--mdui-color-primary-container));
  border-radius: 40px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
}

.project-item {
  display: flex;
  flex-direction: column;
  flex: 1;
  text-decoration: none;
  color: rgb(0, 0, 0);
}

.project-img {
  height: auto;
  width: 100%;
  aspect-ratio: 20 / 9;
}

.project-info {
  padding: 20px 25px;
  flex: 1;
  display: flex;
  flex-direction: column;
  gap: 5px;
}

.project-name {
  font-size: 18px;
  font-weight: bold;
  color: rgb(0, 0, 0);
}

.project-description {
  font-size: 12px;
  font-weight: 600;
  line-height: 1.25;
  opacity: 0.7;
  color: rgba(0, 0, 0, 0.7);
}
@media (prefers-color-scheme: dark) {
  .project-description {
    color: rgb(255, 255, 255);
  }
  .project-name {
    color: rgb(255, 255, 255);
  }
  .project-item {
    color: rgb(255, 255, 255);
  }
}
/* 移动端 */
@media (max-width: 768px) {
  .projects {
    grid-template-columns: 1fr;
  }
}
</style>
