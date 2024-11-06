<template>
  <section id="hero" class="hero">
    <h1>Empowering Future Excellence through Unique Learning Solutions</h1>
    <p>Welcome to PULSE - Punyah Unique Learning Solutions for Excellence...</p>
    <div class="cta-buttons">
      <!-- Use @click to trigger scrollToSection and prevent page redirection -->
      <button @click="scrollToSection('offerings')">Explore Our Offerings</button>
      <button @click="scrollToSection('contact')">Get in Touch</button>
    </div>
  </section>
</template>

<script>
export default {
  methods: {
    // Scroll method with error handling
    scrollToSection(id) {
      const section = document.getElementById(id);
      if (section) {
        section.scrollIntoView({ behavior: "smooth" });
      } else {
        console.warn(`Section with id "${id}" not found.`);
      }
    },
  },
};
</script>

<style scoped>
.hero {
  /* Full viewport width */
  height: 100vh; /* Full viewport height */
  padding: 0; /* Remove padding */
  margin: 0; /* Remove margin */
  text-align: center;
  background: url('@/assets/video.gif') no-repeat center center;
  background-size: cover; /* Cover entire section */
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: center; /* Center content vertically */
  align-items: center; /* Center content horizontally */
  position: relative;
  z-index: 1;
  box-sizing: border-box; /* Ensure padding is within dimensions */
}

/* Semi-transparent dark overlay for better text visibility */
.hero::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5); /* Dark overlay for readability */
  z-index: -1; /* Place overlay behind text */
}

h1 {
  font-size: 3rem;
  font-weight: 700;
  margin-bottom: 1rem;
  line-height: 1.2;
  text-transform: uppercase;
}

p {
  font-size: 1.25rem;
  font-weight: 300;
  margin-bottom: 2rem;
  line-height: 1.6;
}

.cta-buttons {
  margin-top: 2rem;
}

.cta-buttons button {
  margin: 0.5rem;
  padding: 14px 28px;
  border: none;
  border-radius: 30px;
  background: linear-gradient(45deg, #322a2a, #2f2a29);
  color: #fff;
  font-size: 1.2rem;
  font-weight: bold;
  cursor: pointer;
  box-shadow: 0 4px 20px rgba(255, 99, 71, 0.3);
  transition: background 0.3s, transform 0.2s, box-shadow 0.2s;
}

.cta-buttons button:hover {
  background: linear-gradient(45deg, #ff4500, #ff6347);
  transform: translateY(-4px);
  box-shadow: 0 8px 30px rgba(255, 99, 71, 0.5);
}

.cta-buttons button:active {
  transform: translateY(2px);
  box-shadow: 0 4px 15px rgba(255, 99, 71, 0.3);
}

/* Responsive adjustments */
@media (max-width: 768px) {
  h1 {
    font-size: 2.5rem;
  }

  p {
    font-size: 1rem;
  }

  .cta-buttons button {
    font-size: 1rem;
    padding: 10px 20px;
  }
}
</style>
