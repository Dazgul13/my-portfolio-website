<template>
  <section id="contact">
    <div class="container">
      <h2 class="section-title text-center mb-5">Contact Me</h2>
      <div class="row justify-content-center">
        <!-- Map -->
        <div class="col-md-6 map-container mb-4 mb-md-0">
          <iframe
            id="gmap_canvas"
            src="https://maps.google.com/maps?q=centro%20escolar%20university%20manila&t=&z=13&ie=UTF8&iwloc=&output=embed"
            frameborder="0"
            scrolling="no"
            marginheight="0"
            marginwidth="0"
          ></iframe>
        </div>

        <!-- Contact Form -->
        <div class="col-md-6">
          <form @submit.prevent="submitForm" class="contact-form">
            <div class="mb-3">
              <label for="name" class="form-label">Name</label>
              <input
                type="text"
                class="form-control"
                id="name"
                v-model="form.name"
                placeholder="Your name"
                required
              />
            </div>
            <div class="mb-3">
              <label for="email" class="form-label">Email address</label>
              <input
                type="email"
                class="form-control"
                id="email"
                v-model="form.email"
                placeholder="name@example.com"
                required
              />
            </div>
            <div class="mb-3">
              <label for="message" class="form-label">Message</label>
              <textarea
                class="form-control"
                id="message"
                rows="4"
                v-model="form.message"
                placeholder="Write your message here..."
                required
              ></textarea>
            </div>

            <!-- reCAPTCHA -->
            <div class="d-flex justify-content-end mb-3">
              <div ref="recaptchaContainer"></div>
            </div>

            <!-- Submit Button -->
            <button type="submit" class="btn btn-primary w-100">
              {{ isLoading ? "Sending..." : "Send Message" }}
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { ref, onMounted, onBeforeUnmount } from "vue";
import { Notyf } from "notyf";
import "notyf/notyf.min.css";

const WEB3FORMS_ACCESS_KEY = import.meta.env.VITE_WEB3FORMS_ACCESS_KEY;
const SITE_KEY = import.meta.env.VITE_RECAPTCHA_SITE_KEY;

export default {
  name: "ContactSection",
  setup() {
    const notyf = new Notyf();
    const form = ref({
      name: "",
      email: "",
      message: "",
    });
    const isLoading = ref(false);

    // reCAPTCHA
    const recaptchaContainer = ref(null);
    const recaptchaWidgetId = ref(null);
    const recaptchaToken = ref("");

    function onRecaptchaSuccess(token) {
      recaptchaToken.value = token;
    }

    function onRecaptchaExpired() {
      recaptchaToken.value = "";
    }

    function renderRecaptcha() {
      if (!window.grecaptcha) {
        console.error("reCAPTCHA not loaded");
        return;
      }
      recaptchaWidgetId.value = window.grecaptcha.render(
        recaptchaContainer.value,
        {
          sitekey: SITE_KEY,
          size: "normal",
          callback: onRecaptchaSuccess,
          "expired-callback": onRecaptchaExpired,
        }
      );
    }

    function resetRecaptcha() {
      if (recaptchaWidgetId.value !== null) {
        window.grecaptcha.reset(recaptchaWidgetId.value);
        recaptchaToken.value = "";
      }
    }

    // Submit handler
    const submitForm = async () => {
      if (!recaptchaToken.value) {
        notyf.error("Please Verify That You Are Not A Robot.");
        return;
      }

      isLoading.value = true;

      try {
        const response = await fetch("https://api.web3forms.com/submit", {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
            Accept: "application/json",
          },
          body: JSON.stringify({
            access_key: WEB3FORMS_ACCESS_KEY,
            subject: "Contact Form Submission from Portfolio Website",
            name: form.value.name,
            email: form.value.email,
            message: form.value.message,
          }),
        });

        const result = await response.json();

        if (result.success) {
          console.log(result);
          notyf.success("Message Sent!");
          // Reset form
          form.value.name = "";
          form.value.email = "";
          form.value.message = "";
        }
      } catch (error) {
        console.error(error);
        notyf.error("Failed To Send Message");
      } finally {
        isLoading.value = false;
        resetRecaptcha();
      }
    };

    // Lifecycle
    onMounted(() => {
      const interval = setInterval(() => {
        if (window.grecaptcha && window.grecaptcha.render) {
          renderRecaptcha();
          clearInterval(interval);
        }
      }, 100);

      onBeforeUnmount(() => {
        clearInterval(interval);
      });
    });

    return {
      form,
      isLoading,
      recaptchaContainer,
      submitForm,
    };
  },
};
</script>

<style scoped>
.contact-form {
  background-color: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  padding: 2rem;
  border-radius: 15px;
}

.form-control {
  background-color: rgba(255, 255, 255, 0.2);
  border: none;
  color: var(--text-color);
}

.form-control::placeholder {
  color: rgba(255, 255, 255, 0.6);
}

.form-control:focus {
  background-color: rgba(255, 255, 255, 0.3);
  box-shadow: 0 0 0 0.2rem rgba(24, 192, 181, 0.25);
}

.map-container {
  height: 400px;
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

#gmap_canvas {
  width: 100%;
  height: 100%;
}
</style>
