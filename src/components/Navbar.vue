<template>
  <nav id="navbar" :class="{ scrolled: isScrolled }">
    <div class="container">
      <div class="nav-inner">
        <a href="#landing" class="nav-brand">Arjuna Das Espinosa</a>

        <button class="nav-toggle" @click="menuOpen = !menuOpen" aria-label="Toggle navigation">
          <span></span>
          <span></span>
          <span></span>
        </button>

        <ul class="nav-links" :class="{ open: menuOpen }">
          <li><a href="#about" @click="menuOpen = false">About</a></li>
          <li><a href="#projects" @click="menuOpen = false">Projects</a></li>
          <li><a href="#certifications" @click="menuOpen = false">Certifications</a></li>
          <li><a href="#skills" @click="menuOpen = false">Skills</a></li>
          <li><a href="#timeline" @click="menuOpen = false">Timeline</a></li>
          <li><a href="#contact" @click="menuOpen = false">Contact</a></li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'Navbar',
  data() {
    return {
      isScrolled: false,
      menuOpen: false,
    };
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  unmounted() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      this.isScrolled = window.scrollY > 50;
    },
  },
};
</script>
