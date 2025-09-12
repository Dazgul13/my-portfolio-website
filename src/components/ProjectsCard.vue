<script setup>
import { defineProps } from 'vue';

defineProps({
  project: Object,
});
</script>

<template>
  <div class="project-card">
    <img
      :src="project.image"
      class="project-img"
      :alt="project.title"
    />
    <div class="card-body">
      <h3 class="card-title">{{ project.title }}</h3>
      <p class="card-text">{{ project.description }}</p>
      <div class="card-actions">
        <a :href="project.github" target="_blank" class="btn btn-outline-light btn-sm me-2">
          <i class="fab fa-github"></i> GitHub
        </a>
        <a :href="project.demo" target="_blank" class="btn btn-outline-light btn-sm">
          <i class="fas fa-external-link-alt"></i> Demo
        </a>
      </div>
    </div>
  </div>
</template>

<style scoped>
.project-card {
  height: 100%;
  display: flex;
  flex-direction: column;
}

.project-img {
  width: 100%;
  height: 200px;
  object-fit: cover;
}

.card-body {
  flex-grow: 1;
  display: flex;
  flex-direction: column;
}

.card-title {
  font-size: 1.25rem;
  margin-bottom: 0.75rem;
}

.card-text {
  flex-grow: 1;
  margin-bottom: 1rem;
}

.card-actions {
  margin-top: auto;
}

.btn-outline-light {
  border-color: var(--button-color);
  color: var(--button-color);
}

.btn-outline-light:hover {
  background-color: var(--button-color);
  color: var(--button-text-color);
}

.fab, .fas {
  color: var(--icon-color);
}
</style>