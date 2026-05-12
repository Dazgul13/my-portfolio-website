<template>
  <section id="projects">
    <div class="container">
      <div class="section-label">What I've Built</div>
      <h2 class="section-title">Featured Projects</h2>
      <p class="section-subtitle">A selection of my recent work and personal projects.</p>

      <!-- Featured Projects Grid -->
      <div class="projects-featured-grid">
        <ProjectCard
          v-for="project in featuredProjects"
          :key="project.id"
          :project="project"
        />
      </div>

      <!-- Other Projects -->
      <div class="other-projects-title">Other Projects</div>
      <div class="other-projects-grid">
        <div
          v-for="project in otherProjects"
          :key="project.id"
          class="other-project-card"
        >
          <div class="other-project-name">{{ project.title }}</div>
          <div class="other-project-desc">{{ project.description }}</div>
          <div class="other-project-links">
            <a
              v-if="project.github"
              :href="project.github"
              target="_blank"
              rel="noopener"
              class="other-project-link"
            >
              <i class="fab fa-github"></i> Code
            </a>
            <a
              v-if="project.demo"
              :href="project.demo"
              target="_blank"
              rel="noopener"
              class="other-project-link"
            >
              <i class="fas fa-external-link-alt"></i> Demo
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import ProjectCard from './ProjectsCard.vue';
import projects from '../data/projects.json';

// First 4 are featured, rest are "other"
const featuredProjects = projects.filter(p => p.featured);
const otherProjects = projects.filter(p => !p.featured);
</script>
