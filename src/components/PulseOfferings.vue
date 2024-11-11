<template>
  <section id="offerings" class="offerings">  
    <div class="offerings-list">
      <div class="offering-card" v-for="(offering, index) in offerings" :key="index" :class="{ 'reverse-layout': index % 2 !== 0 }">
        <img :src="offering.image" :alt="offering.alt" />
        <div class="content">
          <h3>{{ offering.title }}</h3>
          <p>{{ offering.description }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import studentImage from '@/assets/student.png';
import teacherImage from '@/assets/teacher.png';
import voiceImage from '@/assets/voice.gif';
import endImage from '@/assets/end.gif';

export default {
  name: "PulseOfferings",
  data() {
    return {
      offerings: [
        { image: studentImage, alt: "Student Learning", title: "Personal Experience-Based Learning for Students", description: "Transforming classroom concepts into engaging simulations." },
        { image: teacherImage, alt: "Teacher Content Management", title: "Content and Assessment Management for Teachers", description: "Tools to support teachers in lesson planning and evaluation." },
        { image: voiceImage, alt: "Voice Interface Assessments", title: "Voice Interface-Based Assessments", description: "Students take viva assessments with a humanoid robot." },
        { image: endImage, alt: "End-to-End Recruitment", title: "End-to-End Recruitment Solutions", description: "Comprehensive recruitment readiness for job aspirants, from resume building to interview practice." }
      ]
    };
  }
};
</script>

<style scoped>
/* Section styling */
.offerings {
  padding: 0; /* Remove padding to use full screen space */
  background-color: #eaf7ff; /* Light blue background */
  margin: 0; /* Remove margin */
  width: 100%; /* Make section take up full width */
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1); /* Soft shadow around the section */
}

.offerings h2 {
  text-align: center;
  margin-bottom: 2rem;
  font-size: 2.2rem;
  color: #333; /* Dark text color for better visibility */
}

/* Offerings list grid */
.offerings-list {
  display: flex;
  flex-direction: column;
  margin: 0; /* Remove margin */
  padding: 0; /* Remove padding */
}

/* Card styling */
.offering-card {
  display: flex;
  align-items: center;
  justify-content: space-between; /* Space between content and image */
  padding: 1rem; /* Adjusted padding for no gap */
  color: #fff; /* Light text color */
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  margin: 0; /* Remove gap between cards */
  transition: box-shadow 0.3s ease; /* Removed hover transform effect */
}

/* Card layout alternating colors */
.offering-card:nth-child(even) {
  background-color: #c2b988; /* Deep blue for even cards #31473A, #EDF4F2*/
}

.offering-card:nth-child(odd) {
  background-color: #45535a; /* Coral color for odd cards */
}

/* Alternate image and content layout */
.offering-card.reverse-layout {
  flex-direction: row-reverse;
}

/* Image and GIF styling */
.offering-card img {
  width: 600px; /* Increased image width */
  height: 300px; /* Increased image height */
  object-fit: cover; /* Ensures the image covers the area without distortion */
}

/* Content styling */
.offering-card .content {
  flex: 1;
  padding: 0 1.5rem;
  text-align: left;
}

.offering-card h3 {
  font-size: 2rem; /* Larger heading */
  color: #fff;
  margin-bottom: 0.5rem;
}

.offering-card p {
  color: #ddd;
  margin: 0.5rem 0;
  font-size: 1.1rem; /* Slightly larger text for better readability */
}

/* Responsive styling */
@media (max-width: 768px) {
  .offerings-list {
    gap: 0; /* Remove the gap between cards on mobile */
  }

  .offering-card {
    flex-direction: column;
    text-align: center;
  }

  .offering-card.reverse-layout {
    flex-direction: column;
  }

  .offering-card img {
    width: 100%;
    max-width: 600px; /* Larger image on mobile */
    height: auto;
    margin-bottom: 1rem;
  }

  .offering-card .content {
    padding: 0;
  }
}
</style>
