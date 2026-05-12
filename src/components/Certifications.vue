<template>
  <section id="certifications">
    <div class="container">
      <div class="section-label">Credentials</div>
      <h2 class="section-title">Certifications</h2>
      <p class="section-subtitle">Validating my skills and commitment to continuous learning.</p>

      <div class="certs-grid">
        <div v-for="cert in certifications" :key="cert.id" class="cert-card">
          <div class="cert-title">{{ cert.title }}</div>
          <div class="cert-issuer">{{ cert.issuer }} · {{ cert.year }}</div>
          <a
            v-if="cert.link"
            :href="cert.link"
            target="_blank"
            rel="noopener"
            class="cert-link"
          >
            <i class="fas fa-external-link-alt"></i> View Credential
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Certifications',
  data() {
    return {
      certifications: [
        {
          id: 1,
          title: 'Full Stack Web Development',
          issuer: 'Zuitt Coding Bootcamp',
          year: 'September 25, 2025',
          link: '',
        },
        {
          id: 2,
          title: 'AWS Fundamentals',
          issuer: 'Zuitt Coding Bootcamp',
          year: 'November 7, 2025',
          link: '',
        },
        {
          id: 3,
          title: 'Python Fundamentals',
          issuer: 'Zuitt Coding Bootcamp',
          year: 'May 8, 2026',
          link: '',
        },
        {
          id: 4,
          title: 'Preparatory Course',
          issuer: 'Zuitt Coding Bootcamp',
          year: 'July 4, 2025',
          link: '',
        },
        {
          id: 5,
          title: 'Frontend Course',
          issuer: 'Zuitt Coding Bootcamp',
          year: '2025',
          link: '',
        },
        {
          id: 6,
          title: 'Full Stack Course — MERN',
          issuer: 'Zuitt Coding Bootcamp',
          year: '2025',
          link: '',
        },
      ],
    };
  },
};
</script>
