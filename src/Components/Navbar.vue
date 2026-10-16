<template>
  <header class="navbar" :class="{ scrolled: isScrolled }">
    <div class="nav-container">

      <!-- Logo -->
      <RouterLink to="/#home" class="nav-logo" @click="closeMenu">
        <img src="/images/ccs-logo.png" alt="College of Computer Studies" />
        <div class="logo-text">
          <span>COLLEGE OF</span>
          <strong>COMPUTER STUDIES</strong>
        </div>
      </RouterLink>

      <!-- Desktop Navigation -->
      <nav class="nav-links" :class="{ mobileOpen: menuOpen }">

        <RouterLink
          to="/#home"
          :class="{ active: activeSection === 'home' }"
          @click="closeMenu"
        >
          Home
        </RouterLink>

        <RouterLink
          to="/#programs"
          :class="{ active: activeSection === 'programs' }"
          @click="closeMenu"
        >
          Programs
        </RouterLink>

        <RouterLink
          to="/#faculty"
          :class="{ active: activeSection === 'faculty' }"
          @click="closeMenu"
        >
          Faculty & Staff
        </RouterLink>

        <RouterLink
          to="/#partnerships"
          :class="{ active: activeSection === 'partnerships' }"
          @click="closeMenu"
        >
          Partnerships
        </RouterLink>

      </nav>

      <!-- Mobile Menu -->
      <button
        class="menu-toggle"
        @click="toggleMenu"
        :aria-expanded="menuOpen"
        aria-label="Toggle navigation"
      >
        <span></span>
        <span></span>
        <span></span>
      </button>

    </div>
  </header>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const menuOpen = ref(false)
const isScrolled = ref(false)
const activeSection = ref('home')

const toggleMenu = () => {
  menuOpen.value = !menuOpen.value
}

const closeMenu = () => {
  menuOpen.value = false
}

const handleScroll = () => {
  isScrolled.value = window.scrollY > 40

  const sections = ['home', 'programs', 'faculty', 'partnerships']

  for (const section of sections) {
    const element = document.getElementById(section)

    if (!element) continue

    const rect = element.getBoundingClientRect()

    if (rect.top <= 180 && rect.bottom >= 180) {
      activeSection.value = section
      break
    }
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
  handleScroll()
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 86px;
  z-index: 1000;

  background: rgba(178, 211, 174, 0.96);
  transition: 0.3s ease;

  backdrop-filter: blur(10px);
}

.navbar.scrolled {
  background: #ffffff;
  box-shadow: 0 4px 25px rgba(0, 0, 0, 0.12);
}

.nav-container {
  width: min(1400px, 92%);
  height: 100%;
  margin: auto;

  display: flex;
  align-items: center;
  justify-content: space-between;
}

.nav-logo {
  display: flex;
  align-items: center;
  gap: 12px;

  text-decoration: none;
}

.nav-logo img {
  width: 58px;
  height: 58px;
  object-fit: contain;
}

.logo-text {
  display: flex;
  flex-direction: column;
  line-height: 1.1;
}

.logo-text span {
  font-size: 10px;
  color: #d7d7d7;
  letter-spacing: 2px;
}

.logo-text strong {
  font-size: 14px;
  color: #ffb21b;
  letter-spacing: 1px;
}

.navbar.scrolled .logo-text span {
  color: #173c3c;
}

.nav-links {
  display: flex;
  align-items: center;
  gap: 38px;
}

.nav-links a {
  position: relative;

  padding: 32px 0;

  color: #ffffff;
  text-decoration: none;

  font-size: 16px;
  font-weight: 600;

  transition: 0.3s ease;
}

.nav-links a:hover,
.nav-links a.active {
  color: #ffb21b;
}

.nav-links a::after {
  content: "";

  position: absolute;
  left: 0;
  bottom: 21px;

  width: 0;
  height: 3px;

  background: #ffb21b;

  transition: 0.3s ease;
}

.nav-links a:hover::after,
.nav-links a.active::after {
  width: 100%;
}

.navbar.scrolled .nav-links a {
  color: #173c3c;
}

.navbar.scrolled .nav-links a:hover,
.navbar.scrolled .nav-links a.active {
  color: #f5a900;
}

.menu-toggle {
  display: none;

  border: none;
  background: transparent;

  cursor: pointer;
}

.menu-toggle span {
  display: block;

  width: 28px;
  height: 3px;

  margin: 5px 0;

  background: #ffffff;
}

.navbar.scrolled .menu-toggle span {
  background: #173c3c;
}

@media (max-width: 1000px) {
  .nav-links {
    gap: 20px;
  }

  .nav-links a {
    font-size: 14px;
  }

  .logo-text {
    display: none;
  }
}

@media (max-width: 768px) {
  .navbar {
    height: 75px;
  }

  .nav-logo img {
    width: 52px;
    height: 52px;
  }

  .menu-toggle {
    display: block;
  }

  .nav-links {
    position: absolute;
    top: 75px;
    left: 0;

    width: 100%;

    padding: 15px 25px;

    display: none;
    flex-direction: column;
    gap: 0;

    background: #ffffff;

    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.12);
  }

  .nav-links.mobileOpen {
    display: flex;
  }

  .nav-links a {
    width: 100%;
    padding: 16px 10px;

    color: #173c3c !important;

    text-align: center;
  }

  .nav-links a::after {
    bottom: 8px;
  }
}
</style>