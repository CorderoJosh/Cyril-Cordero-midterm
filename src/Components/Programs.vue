<template>
  <section id="programs" class="programs-section">
    <div class="section-heading">
      <p>ACADEMIC PROGRAMS</p>

      <h2>Programs Offered</h2>

      <div class="heading-line"></div>

      <span>
        Explore the academic programs offered by the College of Computer
        Studies and discover opportunities to build your future in technology.
      </span>
    </div>

    <div class="programs-container">
      <article
        v-for="program in programs"
        :key="program.name"
        class="program-card"
      >
        <div class="program-logo">
          <img
            :src="program.logo"
            :alt="`${program.name} logo`"
            @error="imageError"
          />

          <div class="logo-placeholder">
            {{ program.shortName }}
          </div>
        </div>

        <span class="program-code">
          {{ program.shortName }}
        </span>

        <h3>{{ program.name }}</h3>

        <p>
          {{ program.description }}
        </p>
      </article>
    </div>
  </section>
</template>

<script setup lang="ts">
interface Program {
  name: string
  shortName: string
  description: string
  logo: string
}

const programs: Program[] = [
  {
    name: 'Information Technology',
    shortName: '',
    description:
      'The Bachelor of Science in Information Technology program develops practical skills in software development, information systems, networking, databases, and modern technologies.',
    logo: '/images/bsit-logo.png'
  },
  {
    name: 'Computer Science',
    shortName: '',
    description:
      'The Bachelor of Science in Computer Science program focuses on computing concepts, algorithms, programming, software development, and computer systems.',
    logo: '/images/bsit-logo.png'
  },
  {
    name: 'Digital Media and Interactive Arts',
    shortName: '',
    description:
      'The Bachelor of Science in Digital Media and Interactive Arts program combines creativity and technology through digital media, multimedia, interactive design, and emerging technologies.',
    logo: '/images/bsit-logo.png'
  },
  {
    name: 'Library and Information Science',
    shortName: '',
    description:
      'The Bachelor of Library and Information Science program prepares students in information organization, management, research, digital resources, and library services.',
    logo: '/images/bsit-logo.png'
  }
]

const imageError = (event: Event) => {
  const image = event.target as HTMLImageElement

  image.style.display = 'none'
}
</script>

<style scoped>
.programs-section {
  padding: 120px 5%;


}

.section-heading {
  max-width: 850px;

  margin: 0 auto 70px;

  text-align: center;
}

.section-heading p {
  color: #3222c2;

  font-size: 13px;
  font-weight: 800;

  letter-spacing: 3px;
}

.section-heading h2 {
  margin: 10px 0;

  color: #4dbb22;

  font-size: clamp(38px, 5vw, 58px);
}

.heading-line {
  width: 60px;
  height: 4px;

  margin: 20px auto;

  background: #ffb21b;
}

.section-heading span {
  color: #6f7c7c;

  font-size: 17px;

  line-height: 1.8;
}

.programs-container {
  width: min(1300px, 100%);

  margin: auto;

  display: grid;

  grid-template-columns: repeat(4, 1fr);

  gap: 25px;
}

.program-card {
  min-height: 450px;

  padding: 35px 28px;

  display: flex;
  flex-direction: column;
  align-items: center;

  text-align: center;

  background: #ffffff;

  border: 1px solid #e2e6e6;

  border-radius: 8px;

  box-shadow:
    0 10px 30px rgba(0, 0, 0, 0.07);

  transition: 0.3s ease;
}

.program-card:hover {
  transform: translateY(-8px);

  border-color: #0e2c8f;

  box-shadow:
    0 18px 40px rgba(0, 0, 0, 0.12);
}

.program-logo {
  position: relative;

  width: 140px;
  height: 140px;

  margin-bottom: 20px;

  display: flex;
  align-items: center;
  justify-content: center;
}

.program-logo img {
  max-width: 100%;
  max-height: 100%;

  object-fit: contain;
}



.program-code {
  margin-bottom: 10px;

  color: #ff9f00;

  font-size: 12px;

  font-weight: 800;

  letter-spacing: 2px;
}

.program-card h3 {
  min-height: 60px;

  margin: 0 0 18px;

  color: #083638;

  font-size: 23px;

  line-height: 1.3;
}

.program-card p {
  color: #687575;

  font-size: 14px;

  line-height: 1.8;
}

@media (max-width: 1050px) {
  .programs-container {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 650px) {
  .programs-section {
    padding: 80px 6%;
  }

  .programs-container {
    grid-template-columns: 1fr;
  }

  .program-card {
    min-height: auto;
  }
}
</style>