<script setup>
import { ref, onMounted } from "vue";
import "mdui";
import "mdui/mdui.css";
import { setTheme } from "mdui/functions/setTheme.js";
import "mdui/components/button.js";
import HeaderCard from "./components/HeaderCard.vue";
import { getColorFromImage } from "mdui/functions/getColorFromImage.js";
import { setColorScheme } from "mdui/functions/setColorScheme.js";
import LinksSection from "./components/LinksSection.vue";
import ProgramSection from "./components/ProgramSection.vue";

const config = ref({});
const image = new Image();

onMounted(async () => {
  const response = await fetch("/config.json");
  config.value = await response.json();
  image.src = config.value.avatar;

  if (config.value.theme === "auto") {
    getColorFromImage(image).then((color) => {
      setColorScheme(color);
    });
  } else {
    setColorScheme(config.value.theme);
  }

  setTheme("auto");

  // 更新 meta 信息
  document.title = config.value.name;
  const descriptionMeta = document.querySelector('meta[name="description"]');
  if (descriptionMeta) {
    descriptionMeta.setAttribute("content", config.value.description);
  } else {
    const newMeta = document.createElement("meta");
    newMeta.name = "description";
    newMeta.content = config.value.description;
    document.head.appendChild(newMeta);
  }
});
</script>

<template>
  <div id="main" class="mdui-container">
    <HeaderCard
      :name="config.name"
      :avatar="config.avatar"
      :email="config.email"
      :description="config.description"
    />
    <main class="main-content">
      <div class="info">
        <LinksSection :links="config.links" />
        <ProgramSection :projects="config.projects" />
        <!-- 页脚标签插入位置 -->
        <footer v-html="config.footer" class="footer"></footer>
      </div>
    </main>
  </div>
</template>

<style scoped>
.footer {
  margin-top: 40px;
}
.main-content {
  margin-top: 20px;
  background-color: rgb(var(--mdui-color-secondary-container));
  border-top-left-radius: 40px;
  border-top-right-radius: 40px;
}
.info {
  max-width: 1200px;
  padding: 40px 10%;
  margin: 0 auto;
  border-top-left-radius: 40px;
  border-top-right-radius: 40px;
}

@media (max-width: 768px) {
  .info {
    padding: 40px 3%;
  }
}
</style>
