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
      // Handle form submission logic (e.g., sending data to an API or showing a confirmation)
      console.log("Form submitted with:", this.form);
      // Reset form
      this.form.name = "";
      this.form.email = "";
      this.form.message = "";
      this.showForm = false; // Close the form after submission
    },
    handleClickOutside(event) {
      // Close the form if clicked outside the form and button
      if (
        this.showForm &&
        !this.$refs.contactForm.contains(event.target) &&
        !event.target.closest('.contact-btn')
      ) {
        this.showForm = false; // Close the form
      }
    },
  },
  mounted() {
    // Add event listener when component is mounted
    window.addEventListener("click", this.handleClickOutside);
  },
  beforeUnmount() {
    // Remove event listener when component is destroyed
    window.removeEventListener("click", this.handleClickOutside);
  },
};
</script>

<style scoped>
.about {
  
  color: #333;
  text-align: center;
  position: relative; /* For positioning the button */
}

/* Container for the buttons */
.button-container {
  position: fixed;
  right: 20px;
  bottom: 20px;
  z-index: 20;
  display: flex;
  flex-direction: column;
  gap: 10px; /* Space between buttons */
}

/* Floating Contact Us Button */
.contact-btn {
  background-color: #8acdb2;
  color: white;
  border: none;
  border-radius: 5%;
  padding: 20px;
  font-size: 16px;
  cursor: pointer;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  transform: rotate(90deg); /* Rotated to make it vertical */
  position: fixed;
  right: -30px;
  bottom: 110px; /* Adjusted to place it above WhatsApp button */
  z-index: 15; /* Ensuring it's above the WhatsApp button */
}

.contact-btn:hover {
  background-color: #3f82c9;
}

/* Styling for the contact form */
.contact-form {
  position: fixed;
  top: 50%;
  right: 20px; /* Positioned on the right */
  transform: translateY(-50%); /* Center it vertically */
  width: 100%;
  max-width: 400px;
  background: rgba(255, 255, 255, 0.9);
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  z-index: 19; /* Behind the button */
}

.contact-form h2 {
  margin-bottom: 1.5rem;
  text-align: center;
}

.form-group {
  margin-bottom: 1rem;
}

.form-group label {
  display: block;
  font-weight: bold;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 10px;
  margin-top: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.form-group textarea {
  height: 150px;
  resize: vertical;
}

.submit-btn {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 0.8rem 1.5rem;
  border-radius: 5px;
  cursor: pointer;
  width: 100%;
  margin-top: 1rem;
}

.submit-btn:hover {
  background-color: #0056b3;
}
</style>
