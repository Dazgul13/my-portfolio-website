<script setup>
import Navbar from './components/Navbar.vue';
import LandingSection from './components/LandingSection.vue';
import AboutSection from './components/AboutSection.vue';
import Projects from './components/Projects.vue';
import Certifications from './components/Certifications.vue';
import SkillsSection from './components/SkillsSection.vue';
import Timeline from './components/Timeline.vue';
import References from './components/References.vue';
import Contact from './components/Contact.vue';
import Footer from './components/Footer.vue';
</script>

<template>
  <Navbar />
  <main>
    <LandingSection />
    <AboutSection />
    <Projects />
    <Certifications />
    <SkillsSection />
    <Timeline />
    <References />
    <Contact />
  </main>
  <Footer />
</template>

<style>
/* Remove default body margin/padding that Bootstrap may have added */
body {
  margin: 0;
  padding: 0;
}
</style>
