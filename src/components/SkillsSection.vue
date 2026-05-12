<template>
  <section id="skills">
    <div class="container">
      <div class="section-label">What I Work With</div>
      <h2 class="section-title">Skills & Technologies</h2>
      <p class="section-subtitle">Tools I use to bring ideas to life.</p>

      <div class="skills-grid">
        <div v-for="group in skillGroups" :key="group.title" class="skill-group">
          <div class="skill-group-title">{{ group.title }}</div>
          <ul class="skill-list">
            <li v-for="skill in group.skills" :key="skill">{{ skill }}</li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'SkillsSection',
  data() {
    return {
      skillGroups: [
        {
          title: 'Languages',
          skills: ['HTML5', 'CSS3', 'JavaScript', 'Python'],
        },
        {
          title: 'Frontend',
          skills: ['React.js', 'Vue.js', 'Bootstrap', 'Responsive Web Design'],
        },
        {
          title: 'Backend & DB',
          skills: ['Node.js', 'Express.js', 'Django', 'MongoDB', 'MySQL'],
        },
        {
          title: 'Tools',
          skills: ['Git', 'GitHub', 'GitLab', 'Postman', 'VS Code', 'Sublime Text', 'Trello', 'Figma'],
        },
        {
          title: 'Deployment',
          skills: ['Vercel', 'Render', 'GitHub Pages', 'AWS'],
        },
        {
          title: 'Concepts',
          skills: ['Algorithms', 'Data Structures', 'REST APIs', 'MVC Architecture', 'SDLC'],
        },
      ],
    };
  },
};
</script>
