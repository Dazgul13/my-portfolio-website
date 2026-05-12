<template>
  <section id="timeline">
    <div class="container">
      <div class="section-label">My Journey</div>
      <h2 class="section-title">Timeline</h2>
      <p class="section-subtitle">How I got here.</p>

      <div class="timeline">
        <div v-for="item in timelineItems" :key="item.id" class="timeline-item">
          <div class="timeline-dot"></div>
          <div class="timeline-date">{{ item.date }}</div>
          <div class="timeline-role">{{ item.role }}</div>
          <div class="timeline-org">{{ item.org }}</div>
          <div class="timeline-desc">{{ item.description }}</div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Timeline',
  data() {
    return {
      timelineItems: [
        {
          id: 1,
          date: 'June 2009 – March 2011',
          role: 'Pre-Dentistry',
          org: 'Centro Escolar University, Manila',
          description:
            'Completed pre-dentistry studies, building a strong foundation in the sciences and developing the discipline and attention to detail that carries through all my work.',
        },
        {
          id: 2,
          date: 'June 2011 – March 2016',
          role: 'Doctor of Dental Medicine',
          org: 'Centro Escolar University, Manila',
          description:
            'Earned a Doctor of Dental Medicine degree, developing precision, analytical thinking, and strong patient communication skills.',
        },
        {
          id: 3,
          date: 'April 2017 – November 2017',
          role: 'Technical Support Representative',
          org: 'Telstra Teletech, Pasay, NCR',
          description:
            'Provided technical support and troubleshooting, resolving 85% of tickets and queries. Maintained an 80% customer satisfaction score.',
        },
        {
          id: 4,
          date: 'June 2023 – Present',
          role: 'Sales and Marketing Specialist',
          org: 'GoldenLion Glass and Aluminum Services, Pasig, NCR',
          description:
            'Led direct sales and cultivated client relationships, increasing profits by 15%. Handled operations and logistics, increasing productivity by 20%. Implemented a new system for tracking sales and logistics, improving processing time by 10%.',
        },
        {
          id: 5,
          date: 'September 2024 – July 2025',
          role: 'Executive Sales Agent',
          org: 'OSIVA Electrical Services, Novaliches, NCR',
          description:
            'Achieved sales targets and increased sales by 10%. Provided project documentation and client support, contributing to 20% client retention.',
        },
        {
          id: 6,
          date: 'July 2025 – September 2025',
          role: 'Full-Stack Web Development Certification',
          org: 'Zuitt Coding Bootcamp, Quezon City',
          description:
            'Completed an intensive Tech Career Program covering Git, HTML, CSS, Bootstrap, JavaScript, MongoDB, Node.js, Express.js, Postman, and React.js for full-stack web development. Also covered industry tools such as Figma, ChatGPT, and AWS, as well as Software Development Lifecycles.',
        },
        {
          id: 7,
          date: '2025 – Present',
          role: 'Full-Stack Web Developer',
          org: 'Freelance / Open to Opportunities',
          description:
            'Building real-world web applications using the MERN stack and modern tools. Continuously expanding skills with additional certifications in AWS and Python. Actively seeking full-time opportunities to contribute to impactful products.',
        },
      ],
    };
  },
};
</script>
