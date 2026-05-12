<template>
  <section id="landing">
    <div class="container">
      <div class="hero-inner">
        <div class="hero-text-block">
          <div class="hero-greeting">Hi, my name is</div>
          <h1 class="hero-name">
            <span>ARJUNA DAS</span>
            <span>ESPINOSA</span>
          </h1>
          <div class="hero-role">Full-Stack Web Developer</div>
          <p class="hero-desc">
            Detail-oriented and adaptable Full-Stack Web Developer with certifications in
            Front-End, Back-End, and Full-Stack Development. Strong foundation in algorithms,
            data structures, and coding logic — building real-world web applications that
            connect technical solutions with real business impact.
          </p>
          <div class="hero-actions">
            <a href="#projects" class="btn-primary">
              View My Work
              <i class="fas fa-arrow-down"></i>
            </a>
            <a href="#contact" class="btn-secondary">
              Get In Touch
              <i class="fas fa-envelope"></i>
            </a>
          </div>
          <div class="hero-scroll">
            <div class="hero-scroll-line"></div>
            <span>Scroll</span>
          </div>
        </div>

        <div class="hero-image-wrap">
          <img src="/images/me.jpg" alt="Arjuna Das Espinosa" />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'LandingSection',
};
</script>
