<template>
  <nav class="navbar">
    <div class="logo">
      <img src="@/assets/logo.png" alt="Logo" />
    </div>
  </nav>
</template>

<script>
export default {
  name: "PulseNavbar",
};
</script>

<style scoped>
/* Navbar with transparent background and larger logo */
.navbar {
  display: flex;
  align-items: center;
  padding: 1rem 2rem;
  background: rgba(255, 255, 255, 0); /* Fully transparent background */
  position: fixed;
  width: 100%;
  top: 0;
  /* Optional subtle shadow for visibility */
  z-index: 1000; /* Ensures navbar stays on top */
}

.logo img {
  height: 60px; /* Increased logo size */
  object-fit: contain;
}

/* Responsive adjustments */
@media (max-width: 768px) {
  .navbar {
    padding: 1rem;
  }
  .logo img {
    height: 50px; /* Slightly smaller logo on mobile */
  }
}
</style>
