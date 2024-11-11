<template>
  <section id="hero" class="hero">
    <h1>Empowering Future Excellence through Unique Learning Solutions</h1>
    <p>Welcome to PULSE - Punyah Unique Learning Solutions for Excellence...</p>
  </section>
</template>

<script>
export default {
  methods: {
    // No methods left since there are no buttons
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
  justify-content: flex-start; /* Align the content to the top */
  align-items: center; /* Center content horizontally */
  position: relative;
  z-index: 1;
  box-sizing: border-box; /* Ensure padding is within dimensions */
  padding-top: 50vh; /* Add padding to move text further down */
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

/* Responsive adjustments */
@media (max-width: 768px) {
  h1 {
    font-size: 2.5rem;
  }

  p {
    font-size: 1rem;
  }
}
</style>
