<template>
  <section id="contact">
    <div class="container">
      <div class="section-label">Get In Touch</div>
      <h2 class="section-title">Contact Me</h2>

      <div class="contact-inner">
        <!-- Left: info -->
        <div class="contact-info">
          <p>
            I'm currently open to new opportunities. Whether you have a project in mind,
            a question, or just want to say hi — my inbox is always open.
          </p>
          <div class="contact-links">
            <a href="mailto:arjuna.espinosa13@gmail.com" class="contact-link-item">
              <i class="fas fa-envelope"></i>
              arjuna.espinosa13@gmail.com
            </a>
            <a href="tel:+639179853505" class="contact-link-item">
              <i class="fas fa-phone"></i>
              (+63) 917 985 3505
            </a>
            <a href="https://github.com/Dazgul13" target="_blank" rel="noopener" class="contact-link-item">
              <i class="fab fa-github"></i>
              github.com/Dazgul13
            </a>
            <a href="https://www.linkedin.com/in/arjuna-das-espinosa-8725a8238" target="_blank" rel="noopener" class="contact-link-item">
              <i class="fab fa-linkedin"></i>
              linkedin.com/in/arjuna-das-espinosa
            </a>
          </div>
        </div>

        <!-- Right: form -->
        <form class="contact-form" @submit.prevent="submitForm">
          <div class="form-group">
            <label for="name">Name</label>
            <input
              id="name"
              type="text"
              v-model="form.name"
              placeholder="Your name"
              required
            />
          </div>
          <div class="form-group">
            <label for="email">Email</label>
            <input
              id="email"
              type="email"
              v-model="form.email"
              placeholder="name@example.com"
              required
            />
          </div>
          <div class="form-group">
            <label for="message">Message</label>
            <textarea
              id="message"
              rows="5"
              v-model="form.message"
              placeholder="Write your message here..."
              required
            ></textarea>
          </div>

          <div class="recaptcha-wrap">
            <div ref="recaptchaContainer"></div>
          </div>

          <button type="submit" class="form-submit" :disabled="isLoading">
            {{ isLoading ? 'Sending...' : 'Send Message' }}
          </button>
        </form>
      </div>
    </div>
  </section>
</template>

<script>
import { ref, onMounted, onBeforeUnmount } from 'vue';
import { Notyf } from 'notyf';
import 'notyf/notyf.min.css';

const WEB3FORMS_ACCESS_KEY = import.meta.env.VITE_WEB3FORMS_ACCESS_KEY;
const SITE_KEY = import.meta.env.VITE_RECAPTCHA_SITE_KEY;

export default {
  name: 'ContactSection',
  setup() {
    const notyf = new Notyf();
    const form = ref({ name: '', email: '', message: '' });
    const isLoading = ref(false);
    const recaptchaContainer = ref(null);
    const recaptchaWidgetId = ref(null);
    const recaptchaToken = ref('');

    function onRecaptchaSuccess(token) {
      recaptchaToken.value = token;
    }

    function onRecaptchaExpired() {
      recaptchaToken.value = '';
    }

    function renderRecaptcha() {
      if (!window.grecaptcha) return;
      recaptchaWidgetId.value = window.grecaptcha.render(recaptchaContainer.value, {
        sitekey: SITE_KEY,
        size: 'normal',
        callback: onRecaptchaSuccess,
        'expired-callback': onRecaptchaExpired,
      });
    }

    function resetRecaptcha() {
      if (recaptchaWidgetId.value !== null) {
        window.grecaptcha.reset(recaptchaWidgetId.value);
        recaptchaToken.value = '';
      }
    }

    const submitForm = async () => {
      if (!recaptchaToken.value) {
        notyf.error('Please verify that you are not a robot.');
        return;
      }
      isLoading.value = true;
      try {
        const response = await fetch('https://api.web3forms.com/submit', {
          method: 'POST',
          headers: { 'Content-Type': 'application/json', Accept: 'application/json' },
          body: JSON.stringify({
            access_key: WEB3FORMS_ACCESS_KEY,
            subject: 'Contact Form Submission from Portfolio Website',
            name: form.value.name,
            email: form.value.email,
            message: form.value.message,
          }),
        });
        const result = await response.json();
        if (result.success) {
          notyf.success('Message sent!');
          form.value = { name: '', email: '', message: '' };
        }
      } catch (error) {
        notyf.error('Failed to send message.');
      } finally {
        isLoading.value = false;
        resetRecaptcha();
      }
    };

    onMounted(() => {
      const interval = setInterval(() => {
        if (window.grecaptcha && window.grecaptcha.render) {
          renderRecaptcha();
          clearInterval(interval);
        }
      }, 100);
      onBeforeUnmount(() => clearInterval(interval));
    });

    return { form, isLoading, recaptchaContainer, submitForm };
  },
};
</script>
