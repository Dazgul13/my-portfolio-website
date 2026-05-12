<template>
  <div class="project-card">
    <img
      :src="project.image"
      :alt="project.title"
      class="project-card-img"
    />
    <div class="project-card-body">
      <div v-if="project.type" class="project-card-meta">{{ project.type }}</div>
      <h3 class="project-card-title">{{ project.title }}</h3>
      <p class="project-card-desc">{{ project.description }}</p>
      <div v-if="project.tags && project.tags.length" class="project-tags">
        <span v-for="tag in project.tags" :key="tag" class="tag">{{ tag }}</span>
      </div>
      <div class="project-card-links">
        <a
          v-if="project.github"
          :href="project.github"
          target="_blank"
          rel="noopener"
          class="project-link"
        >
          <i class="fab fa-github"></i> Source Code
        </a>
        <a
          v-if="project.demo"
          :href="project.demo"
          target="_blank"
          rel="noopener"
          class="project-link"
        >
          <i class="fas fa-external-link-alt"></i> Live Demo
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  project: Object,
});
</script>
