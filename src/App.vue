<script setup>
import Navbar from './components/Navbar.vue';
import LandingSection from './components/LandingSection.vue';
import AboutSection from './components/AboutSection.vue';
import Projects from './components/Projects.vue';
import ToolsSection from './components/ToolsSection.vue';
import Contact from './components/Contact.vue';
import Footer from './components/Footer.vue';
</script>

<template>
  <Navbar />
  <div class="container-fluid">
    <LandingSection />
    <AboutSection />
    <Projects />
    <ToolsSection />
    <Contact />
    <Footer />
  </div>
</template>

<style scoped>
/* Add scoped styles here if needed */
</style>