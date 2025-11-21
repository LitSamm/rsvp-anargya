<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const scrolled = ref(false)

function handleScroll() {
  scrolled.value = window.scrollY > 20
}

// URL untuk halaman utama anargya-task - bisa disesuaikan sesuai environment
const MAIN_URL = import.meta.env.VITE_MAIN_URL || 'http://localhost:5173'

function navigateTo(sectionId) {
  const el = document.getElementById(sectionId)
  if (el) {
    el.scrollIntoView({ behavior: 'smooth' })
  }
}

function goToMainPage() {
  // Redirect ke halaman utama anargya-task
  window.location.href = MAIN_URL
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <header class="nav" :class="{ scrolled: scrolled }">
    <a class="brand" href="#">
      <img src="/images/Anargya%20Blacks.png" alt="Anargya ITS EV Team" class="brand-logo" />
      <span class="sr-only">Anargya</span>
    </a>
    <nav class="nav-links">
      <button type="button" @click="goToMainPage">Home</button>
      <button type="button" @click="navigateTo('overview')">Overview</button>
      <button type="button" @click="navigateTo('updates')">Updates</button>
      <button class="launch-link" type="button" @click="navigateTo('rsvp')">RSVP</button>
    </nav>
  </header>
</template>

<style scoped>
/* TOKENS */
:root {
  --bg: #0b0b10;
  --card: rgba(255, 255, 255, 0.06);
  --muted: rgba(255, 255, 255, 0.04);
  --text: #eef2ff;
  --subtext: #b8c1ff;
  --primary: #16a34a;
  --accent: #86efac;
  --bg-glow: rgba(34, 197, 94, 0.18);
}

.nav {
  position: sticky;
  top: 0;
  z-index: 20;
  backdrop-filter: saturate(140%) blur(8px);
  background: linear-gradient(180deg, rgba(11, 11, 16, 0.85), rgba(11, 11, 16, 0.4));
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 12px 20px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
  animation: dropIn 600ms cubic-bezier(.2,.8,.2,1) both;
}

.nav::before {
  content: "";
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--primary), var(--accent), var(--primary));
  background-size: 200% 100%;
  animation: shimmer 4s linear infinite;
  opacity: .9;
}

.nav.scrolled {
  background: linear-gradient(180deg, rgba(11,11,16,.95), rgba(11,11,16,.85));
  border-bottom-color: rgba(255,255,255,.14);
  box-shadow: 0 6px 20px rgba(0,0,0,.25);
}

.brand {
  font-weight: 800;
  letter-spacing: 1px;
  background: linear-gradient(90deg, var(--primary), var(--accent));
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  position: absolute;
  left: 20px;
  font-family: 'Space Grotesk', system-ui, sans-serif;
}

.brand-logo {
  height: 28px;
  width: auto;
  display: block;
}

.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0,0,0,0);
  white-space: nowrap;
  border: 0;
}

.nav-links {
  display: flex;
  align-items: center;
  gap: 14px;
}

.nav-links button {
  margin-left: 14px;
  color: var(--subtext);
  text-decoration: none;
  font-size: 14px;
  position: relative;
  background: transparent;
  border: none;
  font-family: inherit;
  font-weight: inherit;
  cursor: pointer;
  padding: 0;
}

.nav-links button:hover {
  color: var(--text);
}

.nav-links button::after {
  content: "";
  position: absolute;
  left: 0;
  right: 0;
  bottom: -6px;
  height: 2px;
  background: linear-gradient(90deg, var(--primary), var(--accent));
  transform: scaleX(0);
  transform-origin: left;
  transition: transform .25s ease;
}

.nav-links button:hover::after {
  transform: scaleX(1);
}

.toggle {
  margin-left: 14px;
  border: 1px solid rgba(255,255,255,.14);
  background: transparent;
  color: var(--text);
  padding: 6px 10px;
  border-radius: 999px;
  font-weight: 600;
  font-size: 12px;
  cursor: pointer;
}

.nav-links .launch-link {
  border: 1px solid rgba(255, 255, 255, 0.18);
  padding: 6px 14px;
  border-radius: 999px;
  font-weight: 600;
  margin-left: 20px;
  transition: background 0.25s ease, color 0.25s ease, border 0.25s ease;
}

.nav-links .launch-link:hover {
  background: linear-gradient(90deg, var(--primary), var(--accent));
  color: #0b0b10;
  border-color: transparent;
}

@keyframes dropIn {
  from {
    opacity: 0;
    transform: translateY(-10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes shimmer {
  0% {
    background-position: -200% 0;
  }
  100% {
    background-position: 200% 0;
  }
}

@media (max-width: 768px) {
  .nav-links {
    flex-wrap: wrap;
    gap: 8px;
  }
  
  .nav-links button {
    font-size: 12px;
    margin-left: 8px;
  }
  
  .brand-logo {
    height: 24px;
  }
}
</style>

