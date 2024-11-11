<template>
  <section id="about" class="about">
    <!-- Contact Us button (fixed to the bottom-right corner, above the WhatsApp button) -->
    <button class="contact-btn" @click="toggleForm">Contact Us</button>

    <!-- Contact Form (hidden initially, shown when button is clicked) -->
    <div v-if="showForm" class="contact-form" ref="contactForm">
      <h2>Contact Us</h2>

      <!-- Contact Form Fields -->
      <form @submit.prevent="submitForm">
        <div class="form-group">
          <label for="name">Name:</label>
          <input type="text" id="name" v-model="form.name" required />
        </div>

        <div class="form-group">
          <label for="email">Email:</label>
          <input type="email" id="email" v-model="form.email" required />
        </div>

        <div class="form-group">
          <label for="message">Message:</label>
          <textarea id="message" v-model="form.message" required></textarea>
        </div>

        <button type="submit" class="submit-btn">Submit</button>
      </form>
    </div>
  </section>
</template>

<script>
export default {
  name: "ContactUs",
  data() {
    return {
      showForm: false, // Controls visibility of the form
      form: {
        name: "",
        email: "",
        message: "",
      },
    };
  },
  methods: {
    toggleForm() {
      this.showForm = !this.showForm;
    },
    submitForm() {
      // Format the email content
      const subject = "Contact Us Form Submission";
      const body = `Name: ${this.form.name}\nEmail: ${this.form.email}\nMessage: ${this.form.message}`;

      // Create the mailto link
      const mailtoLink = `mailto:contact@ivislabs.com?subject=${encodeURIComponent(subject)}&body=${encodeURIComponent(body)}`;

      // Open the mail client with the pre-filled information
      window.location.href = mailtoLink;

      // Reset form and close it
      this.form.name = "";
      this.form.email = "";
      this.form.message = "";
      this.showForm = false;
    },
    handleClickOutside(event) {
      if (
        this.showForm &&
        !this.$refs.contactForm.contains(event.target) &&
        !event.target.closest(".contact-btn")
      ) {
        this.showForm = false;
      }
    },
  },
  mounted() {
    window.addEventListener("click", this.handleClickOutside);
  },
  beforeUnmount() {
    window.removeEventListener("click", this.handleClickOutside);
  },
};
</script>

<style scoped>
/* General Section Styling */
.about {
  color: #333;
  text-align: center;
  position: relative;
}

/* Contact Button Styling */
.contact-btn {
  background-color: #8acdb2;
  color: white;
  border: none;
  border-radius: 5%;
  padding: 20px;
  font-size: 16px;
  cursor: pointer;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transform: rotate(90deg);
  position: fixed;
  right: -30px;
  bottom: 110px;
  z-index: 15;
}

.contact-btn:hover {
  background-color: #3f82c9;
}

/* Contact Form Styling */
.contact-form {
  position: fixed;
  top: 50%;
  right: 20px;
  transform: translateY(-50%);
  width: 100%;
  max-width: 400px;
  background: rgba(255, 255, 255, 0.9);
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  z-index: 19;
}

.contact-form h2 {
  margin-bottom: 1.5rem;
  text-align: center;
}

/* Form Group Styling */
.form-group {
  margin-bottom: 1.5rem;
}

.form-group label {
  display: block;
  font-weight: bold;
  margin-bottom: 0.5rem;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 12px;
  margin-top: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 14px;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #007bff;
}

.form-group textarea {
  height: 150px;
  resize: vertical;
}

/* Submit Button Styling */
.submit-btn {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 0.8rem 1.5rem;
  border-radius: 5px;
  cursor: pointer;
  width: 100%;
  margin-top: 1rem;
  font-size: 16px;
}

.submit-btn:hover {
  background-color: #0056b3;
}
</style>
