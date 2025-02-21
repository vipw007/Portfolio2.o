<script setup lang="ts">
import { ref } from "vue";

const projects = ref([
  {
    title: "E-Commerce Platform",
    description: "A full-stack online shopping website with payment integration.",
    tech: ["Vue.js", "Spring Boot", "MySQL"],

  },
  {
    title: "Chat Application",
    description: "A real-time chat app using WebSockets for instant messaging.",
    tech: ["Vue.js", "Node.js", "Socket.io"],

  },
  {
    title: "Portfolio Website",
    description: "A personal portfolio built with Vue.js and Tailwind CSS.",
    tech: ["Vue.js", "Tailwind CSS"],

  },
  {
    title: "Task Manager",
    description: "A productivity app to manage daily tasks with notifications.",
    tech: ["Vue.js", "Firebase"],
    
  },
  {
    title: "Covid tracker",
    description: "Tracks covid numbers world wide",
    tech: ["Vue.js", "Firebase"],
    
  },
]);
</script>

<template>
  <section class="projects-section">
    <h1>My Projects</h1>
    <div class="projects-container">
      <div v-for="project in projects" :key="project.title" class="project-card">
        <div class="project-content">
          <h2>{{ project.title }}</h2>
          <p>{{ project.description }}</p>
          <div class="tech-stack">
            <span v-for="tech in project.tech" :key="tech" class="tech">{{ tech }}</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.projects-section {
  width: 100%;
  min-height: 100vh;
  background: url("../assets/about.jpg") no-repeat center center/cover; /* ✅ Background Image */
  color: white;
  text-align: center;
  padding: 50px 20px;
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 30px;
}

/* 🔹 Projects Grid */
.projects-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
  max-width: 1200px;
  margin: auto;
}

/* 🔹 Project Cards */
.project-card {   background: rgba(40, 117, 138, 0.6);
  border-radius: 10px;
  overflow: hidden;
  transition: transform 0.3s ease-in-out;
}

.project-card:hover {
  transform: scale(1.05);
}

.project-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
}

.project-content {
  padding: 15px;
}

h2 {
  font-size: 1.5rem;
  margin-bottom: 10px;
}

p {
  font-size: 1rem;
  margin-bottom: 10px;
  color: #cbd5e1;
}

/* 🔹 Tech Stack */
.tech-stack {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  justify-content: center;
}

.tech {
  background:  rgba(178, 6, 98, 0.6);
  color: #1e293b;
  padding: 5px 10px;
  border-radius: 5px;
  font-size: 0.9rem;
  font-weight: bold;
}
</style>
