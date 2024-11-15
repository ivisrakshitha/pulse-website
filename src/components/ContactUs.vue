<template>
  <section id="about" class="about">
    <!-- Contact Us button (fixed to the bottom-right corner, above the WhatsApp button) -->
    <button class="contact-btn" @click="toggleForm">Contact Us</button>

    <!-- Contact Form (hidden initially, shown when button is clicked) -->
    <div v-if="showForm" class="contact-form" ref="contactForm">
      <!-- Contact Form Header -->
      <div class="form-header">
        <h2>Contact Us</h2>
        <!-- Close Button (X) -->
        <button class="close-btn" @click="closeForm">×</button>
      </div>

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
    closeForm() {
      this.showForm = false; // Close the form when the "X" is clicked
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
  width: 90%; /* Adjusted width to fit smaller screens */
  max-width: 350px;
  background: rgba(255, 255, 255, 0.9);
  padding: 1.5rem;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  z-index: 19;
}

.form-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #007bff;
  color: white;
  padding: 8px;
  border-radius: 3px 3px 0 0;
}

.form-header h2 {
  margin: 0;
  font-size: 16px;
  font-weight: bold;
}

.form-header .close-btn {
  background: none;
  border: none;
  color: white;
  font-size: 22px;
  cursor: pointer;
  font-weight: bold;
  transition: color 0.3s ease;
}

.form-header .close-btn:hover {
  color: #ff4d4d;
}

/* Form Group Styling */
.form-group {
  margin-bottom: 1rem;
}

.form-group label {
  display: block;
  font-weight: bold;
  margin-bottom: 0.5rem;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 10px;
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
  height: 120px;
  resize: vertical;
}

/* Submit Button Styling */
.submit-btn {
  background-color: #007bff;
  color: white;
  border: none;
  padding: 0.6rem 1rem;
  border-radius: 5px;
  cursor: pointer;
  width: 100%;
  margin-top: 1rem;
}

.submit-btn:hover {
  background-color: #0056b3;
}

/* Responsive adjustments for smaller screens */
@media (max-width: 768px) {
  .contact-form {
    top: 15%; /* Position the form further down on smaller screens */
    right: 5%;
    transform: translateY(0);
    width: 90%;
    max-width: 90%;
    padding: 1rem;
  }

  .form-header h2 {
    font-size: 14px;
  }

  .form-header .close-btn {
    font-size: 20px;
  }

  .form-group input,
  .form-group textarea {
    padding: 8px;
    font-size: 13px;
  }

  .submit-btn {
    padding: 0.5rem 0.8rem;
  }
}

@media (max-width: 480px) {
  .contact-form {
    top: 25%; /* Further lower the form for extra small screens */
    width: 95%;
    padding: 0.8rem;
    right: 2.5%;
  }

  .form-header h2 {
    font-size: 12px;
  }

  .form-group input,
  .form-group textarea {
    padding: 6px;
    font-size: 12px;
  }

  .submit-btn {
    padding: 0.5rem 0.7rem;
    font-size: 14px;
  }
}

</style>
