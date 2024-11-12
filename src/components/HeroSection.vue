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
  /* Full viewport width and height */
  height: 100vh;
  padding: 0;
  margin: 0;
  text-align: center;
  background: url('@/assets/video.gif') no-repeat center center;
  background-size: cover;
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: center; /* Center content vertically */
  align-items: center; /* Center content horizontally */
  position: relative;
  z-index: 1;
  box-sizing: border-box;
  padding-top: 20vh; /* Adjust padding to move text down slightly */
}

/* Semi-transparent dark overlay for better text visibility */
.hero::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  z-index: -1;
}

h1 {
  font-size: 3rem;
  font-weight: 700;
  margin: 0 1rem; /* Add margin for horizontal padding */
  line-height: 1.2;
  text-transform: uppercase;
}

p {
  font-size: 1.25rem;
  font-weight: 300;
  margin: 0 1rem; /* Add margin for horizontal padding */
  line-height: 1.6;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  h1 {
    font-size: 2rem;
    line-height: 1.3;
    margin: 0 1rem;
  }

  p {
    font-size: 1rem;
    line-height: 1.4;
    margin: 0 1rem;
  }
}

@media (max-width: 480px) {
  h1 {
    font-size: 1.5rem;
    line-height: 1.2;
    margin: 0 1rem;
  }

  p {
    font-size: 0.9rem;
    line-height: 1.3;
    margin: 0 1rem;
  }
}
</style>
