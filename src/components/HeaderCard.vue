<script setup>
import "mdui/components/button.js";
import "@mdui/icons/email--outlined.js";
import { defineProps } from "vue";

const props = defineProps({
  name: String,
  avatar: String,
  email: String,
  description: String,
});
</script>

<template>
  <header class="header">
    <div class="header-content">
      <div class="avatarName">
        <img :src="avatar" alt="avatar" class="avatar" />
        <h1 class="name">{{ name }}</h1>
      </div>
      <div class="info">
        <p class="description">{{ description }}</p>
        <mdui-button href="mailto:{{ email }}" class="email-button">
          {{ email }}
        </mdui-button>
      </div>
    </div>
  </header>
</template>

<style scoped>
.avatarName {
  align-self: flex-start;
}

.description {
  text-align: left;
  font-size: 15px;
}

.header {
  padding: 60px 20px;
  text-align: center;
}

#info {
  display: flex;
}

.header-content {
  max-width: 1024px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 10px;
}

.avatar {
  width: 180px;
  border-radius: 50%;
}

.name {
  font-size: 36px;
  font-weight: bold;
  text-align: left;
}

.description {
  font-size: 18px;
  text-align: left;
}

.email-button {
  font-weight: bold;
  padding: 10px 20px;
  border-radius: 50px;
  align-self: flex-start;
  display: table;
}
</style>
