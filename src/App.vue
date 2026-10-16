<template>
  <div class="app">

    <Navbar />

    <main>
      <Hero />

      <Programs />

      <Faculty />

      <Partnerships />
    </main>

    <footer class="footer">

      <div class="footer-container">

        <div class="footer-brand">
          <img
            src="/images/ccs-logo.png"
            alt="CCS Logo"
          />

          <div>
            <h3>College of Computer Studies</h3>
            <p>
              Central Philippine University
            </p>
          </div>
        </div>

        <div class="footer-links">
          <a href="#home">Home</a>
          <a href="#programs">Programs</a>
          <a href="#faculty">Faculty & Staff</a>
          <a href="#partnerships">Partnerships</a>
        </div>

      </div>

      <div class="footer-bottom">
        <p>
          © {{ currentYear }} College of Computer Studies.
          All Rights Reserved.
        </p>

        <p>
          Scientia et Fides
        </p>
      </div>

    </footer>

  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue'

import Navbar from './Components/Navbar.vue'
import Hero from './Components/Hero.vue'
import Programs from './Components/Programs.vue'
import Faculty from './Components/Faculty.vue'
import Partnerships from './Components/Partnerships.vue'

const currentYear = computed(() => new Date().getFullYear())
</script>