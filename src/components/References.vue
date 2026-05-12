<template>
  <section id="references">
    <div class="container">
      <div class="section-label">People Who Helped Me</div>
      <h2 class="section-title">References</h2>
      <p class="section-subtitle">Mentors and professionals who supported my journey into tech.</p>

      <div class="references-grid">
        <div v-for="ref in references" :key="ref.id" class="reference-card">
          <div>
            <div class="reference-name">{{ ref.name }}</div>
            <div class="reference-role">{{ ref.role }}</div>
            <div class="reference-org">{{ ref.org }}</div>
          </div>
          <a
            v-if="ref.linkedin"
            :href="ref.linkedin"
            target="_blank"
            rel="noopener"
            class="other-project-link"
            style="margin-top: 0.5rem;"
          >
            <i class="fab fa-linkedin"></i> LinkedIn
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'References',
  data() {
    return {
      references: [
        {
          id: 1,
          name: 'Matthew Ramon Raga',
          role: 'Lead Instructor',
          org: 'Zuitt Coding Bootcamp',
          linkedin: '',
        },
        {
          id: 2,
          name: 'Luis Paolo San Gabriel',
          role: 'Instructor',
          org: 'Zuitt Coding Bootcamp',
          linkedin: '',
        },
        
      ],
    };
  },
};
</script>
