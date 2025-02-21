<script setup lang="ts">
import { ref, onMounted } from "vue";

const skills = ref([
  { name: "Spring Boot", percentage: 80 },
  { name: "Vue.js, HTML, CSS, JavaScript", percentage: 90 },
  { name: "C++, JavaScript, Java, MySQL", percentage: 90 },
  { name: "Machine Learning", percentage: 70 },
  { name: "DSA", percentage: 80 },
  { name: "Postman, Jira, Confluence, Git", percentage: 95 },
]);

const animate = ref(false);

onMounted(() => {
  animate.value = true;
});

// Resume file path (place resume.pdf in /public folder)
const resumeUrl = "/resume.pdf";
</script>

<template>
  <section class="about-section">
    <div class="overlay">
      <div class="content">
        <h1>About Me</h1>
        <p>I am a passionate developer specializing in backend and frontend technologies.</p>

        <div class="skills">
          <h2>Skills</h2>
          <div v-for="skill in skills" :key="skill.name" class="skill">
            <span class="skill-name">{{ skill.name }}</span>
            <div class="progress-bar">
              <div class="progress" :style="{ width: animate ? skill.percentage + '%' : '0%' }">
                {{ skill.percentage }}%
              </div>
            </div>
          </div>
        </div>

        <!-- ✅ Resume Section -->
        <div class="resume-section">
          <h2>My Resume</h2>
          <p>Download my resume to learn more about my experience and skills.</p>
          <a :href="resumeUrl" download="My_Resume.pdf" class="download-button">Download Resume</a>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about-section {
  width: 100%;
  min-height: 100vh;
  background: url("../assets/about.jpg") no-repeat center center/cover;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  position: relative;
  padding: 50px 20px;
}

/* 🔹 Overlay for better text visibility */
.overlay {
  width: 100%;
  height: 100%;
  background: rgba(40, 117, 138, 0.6);
  display: flex;
  align-items: center;
  justify-content: center;
}

.content {
  max-width: 600px;
  color: white;
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 10px;
}

p {
  font-size: 1.2rem;
  margin-bottom: 30px;
}

/* 🔹 Skills Section */
.skills h2 {
  font-size: 2rem;
  margin-bottom: 20px;
}

.skill {
  margin-bottom: 15px;
}

.skill-name {
  font-size: 1.2rem;
  font-weight: bold;
  display: block;
  margin-bottom: 5px;
}

/* 🔹 Progress Bar */
.progress-bar {
  width: 100%;
  height: 25px;
  background: rgba(255, 255, 255, 0.3);
  border-radius: 20px;
  overflow: hidden;
}

.progress {
  height: 100%;
  background:  rgba(187, 99, 146, 0.6); /* 🔸 Orange color */
  color: white;
  font-size: 1rem;
  text-align: center;
  line-height: 25px;
  font-weight: bold;
  transition: width 1.5s ease-in-out;
}

/* ✅ Resume Section */
.resume-section {
  margin-top: 50px;
}

.download-button {
  background: #f59e0b;
  color: #1e293b;
  padding: 12px 20px;
  font-size: 1.2rem;
  font-weight: bold;
  text-decoration: none;
  border-radius: 8px;
  transition: background 0.3s ease;
  display: inline-block;
}

.download-button:hover {
  background: #ffaf38;
}
</style>
