<template>
  <footer>
    <div class="footer">
      <div class="footer-logo logo footer-item">
        <img src="@/assets/logo_transparent_small.png" alt="Logo" />
        <h2>Intelligent Vision Labs</h2>
      </div>
      <div class="navigation footer-item">
        <ul>
          <li><a href="index.html">Home</a></li>
          <li><a href="solution.html">Our Solutions</a></li>
        </ul>
      </div>
      <div class="contact-div footer-item">
        <div class="contacts">
          <img src="@/assets/phone.svg" alt="Phone" width="20" />
          <a href="tel:+919449963312">+91 9449963312</a>
        </div>
        <div class="location footer-item">
          <img src="@/assets/location.svg" alt="Location" width="20" />
          <span>113/A, 1st floor, 7th cross, Temple road, Jayalakshmipuram, Mysuru -570012</span>
        </div>
      </div>
      <div class="socials footer-item">
        <ul class="social-icons">
          <li class="icon-content">
            <a href="https://www.linkedin.com/company/punyahacademy/posts/?feedView=all" aria-label="LinkedIn" data-social="linkedin">
              <img src="@/assets/linkedin.png" alt="LinkedIn" />
            </a>
            <div class="tooltip">LinkedIn</div>
          </li>
          <li class="icon-content">
            <a href="https://www.instagram.com/pulse.ivislabs/" aria-label="Instagram" data-social="instagram">
              <img src="@/assets/instagram.png" alt="Instagram" />
            </a>
            <div class="tooltip">Instagram</div>
          </li>
          <li class="icon-content">
            <a href="mailto:contact@ivislabs.com" aria-label="Gmail" data-social="gmail">
              <img src="@/assets/mail.png" alt="Mail" />
            </a>
            <div class="tooltip">Gmail</div>
          </li>
        </ul>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'FooteR'
};
</script>

<style scoped>
.footer {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1.5rem;
  padding: 2rem;
  color: #6c757d;
  font-family: "Roboto", sans-serif;
  background-color:#dadbdc; /* Light background color */
}

.footer-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  padding: 10px;
}

.footer-logo img {
  width: 60px;
  margin-bottom: 0.5rem;
}

.footer-logo h2 {
  font-size: 1.25rem;
  font-weight: 600;
  color: #333;
}

.navigation ul,
.social-icons {
  list-style-type: none;
  padding: 0;
}

.navigation ul li,
.social-icons li {
  margin-bottom: 10px;
}

.navigation ul li a {
  text-decoration: none;
  color: #6c757d;
  font-size: 0.875rem;
  transition: color 0.3s;
}

.navigation ul li a:hover {
  color: #007bff;
}

.contacts, .location {
  display: flex;
  align-items: center;
  gap: 10px;
}

.socials .social-icons {
  display: flex;
  gap: 20px;
}

.icon-content img {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  padding: 8px;
  background-color: #007bff;
  transition: transform 0.3s;
}

.icon-content:hover img {
  transform: scale(1.1);
}

.tooltip {
  visibility: hidden;
  background-color: #333;
  color: #fff;
  text-align: center;
  border-radius: 5px;
  padding: 5px;
  position: absolute;
  z-index: 1;
  top: 100%;
  left: 50%;
  transform: translateX(-50%);
  font-size: 0.75rem;
  opacity: 0;
  transition: opacity 0.3s;
}

.icon-content:hover .tooltip {
  visibility: visible;
  opacity: 1;
}

@media (max-width: 768px) {
  .footer {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .footer-logo h2 {
    font-size: 1rem;
  }

  .navigation ul li a, .contacts a {
    font-size: 0.875rem;
  }

  .icon-content img {
    width: 32px;
    height: 32px;
  }
}
</style>
