<template>
  <section id="testimonials" class="testimonials">
    <h2>Our Verticals</h2>
    
    <!-- Navigation Links for Carousel Headings -->
    <div class="carousel-navigation">
      <span
        v-for="(video, index) in testimonials"
        :key="index"
        @click="goToTestimonial(index)"
        :class="{ active: currentTestimonial === index }"
      >
        {{ video.heading }}
      </span>
    </div>
    
    <!-- Carousel Content for Video Links -->
    <div class="carousel">
      <div
        class="video-card"
        v-for="(video, index) in testimonials"
        :key="index"
        v-show="currentTestimonial === index"
      >
        <img :src="video.thumbnail" :alt="video.heading" @click="playVideo(video.url)" />
      </div>
    </div>
  </section>
</template>

<script>
// Import local images for other videos; use a direct link for S3 thumbnail.
import assessmentsThumbnail from '@/assets/Assessments.gif';
import robotBasedThumbnail from '@/assets/Robot-Based.gif';

// Replace this with the publicly accessible URL or pre-signed URL for S3
const jobReadinessThumbnail = 'https://ivislabsdocs.s3.ap-south-1.amazonaws.com/pulsewebsite/Job-Readyness-Program.gif';

export default {
  name: "PulseTestimonials",
  data() {
    return {
      testimonials: [
        { heading: "Assessments", thumbnail: assessmentsThumbnail, url: "https://example.com/assessments-video" },
        { heading: "Robot-Based", thumbnail: robotBasedThumbnail, url: "https://example.com/robot-video" },
        { heading: "Job Readiness Program", thumbnail: jobReadinessThumbnail, url: "https://example.com/job-readiness-video" },
      ],
      currentTestimonial: 0,
    };
  },
  methods: {
    goToTestimonial(index) {
      this.currentTestimonial = index;
    },
    playVideo(url) {
      window.open(url, "_blank"); // Opens the video in a new tab
    },
  },
};
</script>

<style scoped>
.testimonials {
  padding: 2rem;
  background-color: #c8e1ee;
}

.testimonials h2 {
  text-align: center;
  margin-bottom: 1.5rem;
}

.carousel-navigation {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-bottom: 1rem;
}

.carousel-navigation span {
  cursor: pointer;
  padding: 0.5rem 1rem;
  color: #000;
  transition: color 0.3s ease;
}

.carousel-navigation span:hover {
  color: #555;
}

.carousel-navigation .active {
  text-decoration: underline;
}

.carousel {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  max-width: 100%;
  margin: 0 auto;
  overflow: hidden;
}

.video-card {
  background-color: transparent;
  padding: 1rem;
  border-radius: 8px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  text-align: center;
  display: flex;
  flex-direction: column;
  transition: opacity 0.3s ease;
  max-width: 100%;
}

.video-card img {
  width: 100%;
  height: auto;
  max-width: 800px;
  border-radius: 8px;
  cursor: pointer;
}

.video-info {
  text-align: center;
  margin-top: 1rem;
  font-weight: bold;
}
</style>
