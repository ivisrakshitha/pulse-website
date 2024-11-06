<template>
  <div id="app">
    <!-- Hero Section -->
    <PulseNavbar />
    <HeroSection />

    <!-- About Us Section -->
     

    <!-- Offerings Section -->
    <PulseOfferings id="offerings" />

    <!-- How It Works Section -->

    <!-- Testimonials Section -->
    <PulseTestimonials />
    <WhatsApp/>
    <ContactUs/>

    <!-- Contact Us Section -->
    <FooteR/>
  </div>
</template>

<script>
import PulseNavbar from "./components/Navbar.vue";
import HeroSection from "./components/HeroSection.vue";
import PulseOfferings from "./components/PulseOfferings.vue";
import PulseTestimonials from "./components/PulseTestimonials.vue";
import FooteR from "./components/FooteR.vue";  // Corrected this line
import ContactUs from "./components/ContactUs.vue";
import WhatsApp from "./components/WhatsApp.vue";
 
export default {
  components: {
    PulseNavbar,
    HeroSection,
    PulseOfferings,
    PulseTestimonials,
    FooteR,  // Corrected this line
    ContactUs,
    WhatsApp,
  },
  methods: {
    scrollTo(sectionId) {
      const section = document.getElementById(sectionId);
      if (section) {
        section.scrollIntoView({ behavior: "smooth" });
      }
    },
  },
};
</script>

<style>
/* Basic styling for layout and responsiveness */

*{
  margin: 0;
  padding: 0;
}

#app {
  font-family: Arial, sans-serif;
  text-align: center;
  color: #333;
}

.hero {
  background: #f4f4f4;
  padding: 60px 20px;
}

.hero h1 {
  font-size: 2.5em;
  margin-bottom: 10px;
}

.hero p {
  font-size: 1.2em;
  max-width: 700px;
  margin: 0 auto 20px;
}

.cta-buttons button {
  margin: 0 10px;
  padding: 10px 20px;
  font-size: 1em;
  cursor: pointer;
}

 
</style>
