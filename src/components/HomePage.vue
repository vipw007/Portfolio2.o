<script setup lang="ts">
import { ref, onMounted } from "vue";


const fadeIn = ref(false);



 
const scrollToProjects = () => {
  const projectsSection = document.getElementById("projects");
  if (projectsSection) {
    projectsSection.scrollIntoView({ behavior: "smooth" });
  }

}
onMounted(() => {
  fadeIn.value = true;
});

</script>

<template>
  <section id="home" class="home-section">
    <div class="overlay">
      <h1>Hi I'm Vivek Kumar Yadav </h1>
      <p>Welcome to My Portfolio ,I'm a Vue.js Developer passionate about building awesome web applications.</p>
      <button class="cta-button"  @click="scrollToProjects">Explore My Work</button>
    </div>
  </section>
</template>

<style scoped>
.home-section {
  height: 100vh; /* Full screen height */
  width: 100vw; /* Full screen width */
  background: url("../assets/about.jpg") no-repeat center center/cover; /* ✅ Background Image */
  background-size: cover;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  color: white;
  position: relative;
  overflow: hidden;
  margin: 0;
  padding: 0;
}

.overlay {
  background: rgba(187, 99, 146, 0.6);
  padding: 2rem;
  border-radius: 10px;
  max-width: 80%;
  text-align: center;
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 10px;
}

p {
  font-size: 1.2rem;
  margin-bottom: 20px;
}

.cta-button {
  background: white;
  color: #1e3a8a;
  border: none;
  padding: 10px 20px;
  font-size: 1.2rem;
  cursor: pointer;
  border-radius: 5px;
  transition: background 0.3s ease;
}

.cta-button:hover {
  background: #e0e7ff;
}
</style>
