<script setup lang="ts">
import { ref } from "vue";

import HomePage from "./components/HomePage.vue";
import AboutPage from "./components/AboutPage.vue";
import Project from "./components/Project.vue"; 
import Contact from "./components/Contact.vue";

const menuOpen = ref(false);

const toggleMenu = () => {
  menuOpen.value = !menuOpen.value;
};

const scrollToSection = (id: string) => {
  menuOpen.value = false; // Close menu on navigation
  const section = document.getElementById(id);
  if (section) {
    section.scrollIntoView({ behavior: "smooth" });
  }
};
</script>

<template>
  <header class="navbar">
    <div class="brand" @click.prevent="scrollToSection('home')">Portfolio</div>
    
    <nav :class="{ open: menuOpen }">
      <ul>
        <li><a @click.prevent="scrollToSection('home')">Home</a></li>
        <li><a @click.prevent="scrollToSection('about')">About</a></li>
        <li><a @click.prevent="scrollToSection('projects')">Projects</a></li>
        <li><a @click.prevent="scrollToSection('contact')">Contact</a></li>
      </ul>
    </nav>

    <!-- Hamburger Button -->
    <div class="hamburger" @click="toggleMenu">
      <span></span>
      <span></span>
      <span></span>
    </div>
  </header>

  <main>
    <section id="home">
      <HomePage />
    </section>
    <section id="about" > <AboutPage/> </section>
    <section id="projects" class="section"><Project/> </section>
    <section id="contact" class="section"> <Contact/> </section>
  </main>
</template>

<style scoped>
/* 🔹 General Styles */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html, body {
  width: 100%;
  height: 100%;
  overflow-x: hidden; /* Prevents horizontal scroll */
}

/* 🔹 Navbar */
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background: #282c34; /* Dark grayish-blue */
  color: white;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 20px;
  z-index: 1000;
}

/* 🔹 Brand Name */
.brand {
  font-size: 1.5rem;
  font-weight: bold;
  cursor: pointer;
  transition: color 0.3s ease;
}

.brand:hover {
  color: #ff8800; /* Orange hover effect */
}

/* 🔹 Navbar Menu */
nav {
  display: flex;
}

nav ul {
  display: flex;
  gap: 20px;
  list-style: none;
}

nav ul li a {
  color: white;
  text-decoration: none;
  font-size: 18px;
  cursor: pointer;
  padding: 8px 12px;
  border-radius: 5px;
  transition: background 0.3s ease, color 0.3s ease;
}

nav ul li a:hover {
  background: #ff8800; /* Orange */
  color: white;
}

/* 🔹 Hamburger Menu (Mobile) */
.hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  cursor: pointer;
}

.hamburger span {
  display: block;
  width: 25px;
  height: 3px;
  background: white;
  transition: all 0.3s ease;
}

/* 🔹 Mobile Menu */
@media (max-width: 768px) {
  nav {
    position: absolute;
    top: 60px;
    right: 0;
    background: rgba(40, 44, 52, 0.95);
    flex-direction: column;
    width: 200px;
    display: none;
    border-radius: 5px;
  }

  nav.open {
    display: flex;
  }

  nav ul {
    flex-direction: column;
    text-align: right;
    padding: 10px 0;
    padding-right: 60px;
  }

  nav ul li {
    padding: 10px;
  }

  /* 🔹 Hamburger Icon */
  .hamburger {
    display: flex;
  }

  .hamburger span {
    background: #ff8800; /* Orange color */
  }

  .hamburger:hover span {
    background: white;
  }
}
</style>

