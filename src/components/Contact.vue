<script setup lang="ts">
import { ref } from "vue";
import emailjs from "@emailjs/browser"; // Import EmailJS

const form = ref({
  name: "",
  email: "",
  message: "",
});

const errors = ref({
  name: "",
  email: "",
  message: "",
});

const validateEmail = (email: string) => {
  return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
};

const sendMessage = async () => {
  errors.value = { name: "", email: "", message: "" };

  if (!form.value.name) errors.value.name = "Name is required.";
  if (!form.value.email) {
    errors.value.email = "Email is required.";
  } else if (!validateEmail(form.value.email)) {
    errors.value.email = "Invalid email format.";
  }
  if (!form.value.message) errors.value.message = "Message cannot be empty.";

  if (!errors.value.name && !errors.value.email && !errors.value.message) {
    try {
      const response = await emailjs.send(
        "service_dba5bne", // Replace with your EmailJS Service ID
        "template_apnz8tf", // Replace with your EmailJS Template ID
        {
          name: form.value.name,
          email: form.value.email,
          message: form.value.message,
        },
        "V5yNkinBVjbCY7DKh" // Replace with your EmailJS Public Key
      );

      if (response.status === 200) {
        alert("Message sent successfully!");
        form.value = { name: "", email: "", message: "" }; // Reset form
      }
    } catch (error) {
      console.error("Email sending error:", error);
      alert("Failed to send message. Please try again later.");
    }
  }
};
</script>

<template>
  <section class="contact-section">
    <h1>Contact Me</h1>
    <p>Feel free to reach out for any inquiries or collaborations.</p>

    <form @submit.prevent="sendMessage">
      <div class="input-group">
        <label for="name">Name</label>
        <input v-model="form.name" type="text" id="name" placeholder="Enter your name" />
        <span class="error">{{ errors.name }}</span>
      </div>

      <div class="input-group">
        <label for="email">Email</label>
        <input v-model="form.email" type="email" id="email" placeholder="Enter your email" />
        <span class="error">{{ errors.email }}</span>
      </div>

      <div class="input-group">
        <label for="message">Message</label>
        <textarea v-model="form.message" id="message" placeholder="Type your message"></textarea>
        <span class="error">{{ errors.message }}</span>
      </div>

      <button type="submit">Send Message</button>
    </form>

    <div class="social-links">
      <a href="https://github.com/vivekyadav07" target="_blank">GitHub</a>
      <a href="https://linkedin.com/in/vivek-yadav-126860102" target="_blank">LinkedIn</a>
      <a href="vivekkumaryadav97@gmail.com">Email</a>
    </div>
  </section>
</template>

<style scoped>
.contact-section {
  width: 100%;
  min-height: 100vh;
  background: url("../assets/about.jpg") no-repeat center center/cover; /* ✅ Background Image */
  color: white;
  text-align: center;
  padding: 50px 20px;
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 10px;
}

p {
  font-size: 1.2rem;
  margin-bottom: 30px;
}

form {
  max-width: 500px;
  margin: auto;
  background: rgba(187, 99, 146, 0.6);
  padding: 20px;
  border-radius: 10px;
}

.input-group {
  margin-bottom: 15px;
  text-align: left;
}

label {
  display: block;
  font-size: 1rem;
  margin-bottom: 5px;
}

input,
textarea {
  width: 100%;
  padding: 10px;
  border: none;
  border-radius: 5px;
  font-size: 1rem;
}

textarea {
  height: 100px;
}

button {
  width: 100%;
  background: #f59e0b; /* 🔸 Orange button */
  color: #1e293b;
  border: none;
  padding: 10px;
  font-size: 1.2rem;
  cursor: pointer;
  border-radius: 5px;
  transition: background 0.3s ease;
}

button:hover {
  background: #ffaf38;
}

/* 🔹 Error Messages */
.error {
  color: red;
  font-size: 0.9rem;
}

/* 🔹 Social Links */
.social-links {
  margin-top: 20px;
}

.social-links a {
  color: #f59e0b;
  text-decoration: none;
  margin: 0 10px;
  font-size: 1.2rem;
}

.social-links a:hover {
  color: #ffaf38;
}
</style>
