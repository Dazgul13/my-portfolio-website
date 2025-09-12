<template>
    <!-- My Projects Section -->
    <section class="pb-5" id="projects">
        <!-- Section Heading -->
        <h1 class="mt-5 mb-5 pb-4 text-center">My Projects</h1>

        <div class="row">
            <div
                v-for="project in paginatedProjects"
                :key="project.id"
                class="col-12 col-md-6 col-lg-4 mb-4"
            >
                <ProjectCard :project="project" />
            </div>
        </div>
        <div v-if="totalPages > 1" class="pagination d-flex justify-content-center mt-4">
            <button @click="prevPage" :disabled="currentPage === 1" class="btn btn-primary me-2">Previous</button>
            <span class="align-self-center mx-2">Page {{ currentPage }} of {{ totalPages }}</span>
            <button @click="nextPage" :disabled="currentPage === totalPages" class="btn btn-primary ms-2">Next</button>
        </div>
    </section>
</template>

<script setup>
import { ref, computed } from 'vue';
import ProjectCard from './ProjectsCard.vue';
import projects from '../data/projects.json';

const currentPage = ref(1);
const projectsPerPage = 9;

const paginatedProjects = computed(() => {
  const start = (currentPage.value - 1) * projectsPerPage;
  const end = start + projectsPerPage;
  return projects.slice(start, end);
});

const totalPages = computed(() => Math.ceil(projects.length / projectsPerPage));

function nextPage() {
  if (currentPage.value < totalPages.value) {
    currentPage.value++;
  }
}

function prevPage() {
  if (currentPage.value > 1) {
    currentPage.value--;
  }
}
</script>