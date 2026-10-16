<template>
  <section id="partnerships" class="partnership-section">
    <div class="section-heading">
      <p>CONNECTED BEYOND THE CLASSROOM</p>

      <h2>Partnerships & Memberships</h2>

      <div class="heading-line"></div>

      <span>
        Building meaningful connections with professional organizations,
        industry partners, academic communities, and technology groups.
      </span>
    </div>

    <div class="partners-container">
      <article
        v-for="partner in partners"
        :key="partner.name"
        class="partner-card"
      >
        <div class="partner-logo">
          <img
            :src="partner.logo"
            :alt="partner.name"
            @error="imageError"
          />

          <div class="logo-placeholder">
            {{ partner.shortName }}
          </div>
        </div>

        <h3>{{ partner.name }}</h3>

        <p>{{ partner.description }}</p>

        <span class="partner-type">
          {{ partner.type }}
        </span>
      </article>
    </div>

    <div class="partnership-message">
      <div>
        <span>REMEMBER • CONNECT • ENGAGE</span>

        <h3>Different People, One Goal.</h3>
      </div>

      <p>
        Through partnerships and professional memberships, CCS continues
        to connect students and educators with communities beyond the
        classroom.
      </p>
    </div>
  </section>
</template>

<script setup lang="ts">
interface Partner {
  name: string
  shortName: string
  type: string
  description: string
  logo: string
}

const partners: Partner[] = [
  {
    name: 'Computer Science Society',
    shortName: 'CSS',
    type: 'Membership',
    description:
      'A student-centered organization that promotes collaboration, learning, and professional development.',
    logo: '/images/partners/computer-science-society.png'
  },
  {
    name: 'Information Technology Students Organization',
    shortName: 'ITSO',
    type: 'Membership',
    description:
      'A community that supports information technology students through activities and professional growth.',
    logo: '/images/partners/itso.png'
  },
  {
    name: 'MIDAS',
    shortName: 'MIDAS',
    type: 'Membership',
    description:
      'A community supporting digital media, interactive arts, creativity, and technology.',
    logo: '/images/partners/midas.png'
  },
  {
    name: 'Library and Information Science Organization',
    shortName: 'LISO',
    type: 'Membership',
    description:
      'An organization that promotes information management, library science, and professional development.',
    logo: '/images/partners/liso.png'
  }
]

const imageError = (event: Event) => {
  const image = event.target as HTMLImageElement

  image.style.display = 'none'
}
</script>

<style scoped>
.partnership-section {
  padding: 120px 5%;

  background:
    linear-gradient(
      135deg,
      #67a7aa,
      #65caac
    );

  color: #ffffff;
}

.section-heading {
  max-width: 850px;

  margin: 0 auto 70px;

  text-align: center;
}

.section-heading p {
  color: #ffb21b;

  font-size: 13px;
  font-weight: 800;

  letter-spacing: 3px;
}

.section-heading h2 {
  margin: 10px 0;

  font-size: clamp(38px, 5vw, 58px);
}

.heading-line {
  width: 60px;
  height: 4px;

  margin: 20px auto;

  background: #ffb21b;
}

.section-heading span {
  color: #c5d0d0;

  font-size: 17px;
  line-height: 1.8;
}

.partners-container {
  width: min(1300px, 100%);

  margin: auto;

  display: grid;

  grid-template-columns: repeat(4, 1fr);

  gap: 25px;
}

.partner-card {
  min-height: 390px;

  padding: 35px 25px;

  display: flex;
  flex-direction: column;
  align-items: center;

  text-align: center;

  background: rgba(255, 255, 255, 0.07);

  border: 1px solid rgba(255, 255, 255, 0.12);

  border-radius: 7px;

  transition: 0.3s ease;
}

.partner-card:hover {
  transform: translateY(-8px);

  background: rgba(255, 255, 255, 0.12);

  border-color: #ffb21b;
}

.partner-logo {
  position: relative;

  width: 150px;
  height: 150px;

  margin-bottom: 25px;

  display: flex;
  justify-content: center;
  align-items: center;
}

.partner-logo img {
  max-width: 100%;
  max-height: 100%;

  object-fit: contain;
}

.logo-placeholder {
  position: absolute;

  width: 110px;
  height: 110px;

  display: flex;
  align-items: center;
  justify-content: center;

  border-radius: 50%;

  background: #ffffff;

  color: #123b3c;

  font-size: 18px;
  font-weight: 900;

  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
}

.partner-card h3 {
  min-height: 55px;

  margin: 0 0 15px;

  font-size: 20px;
}

.partner-card p {
  color: #c2cccc;

  font-size: 14px;

  line-height: 1.7;
}

.partner-type {
  margin-top: auto;

  color: #ffb21b;

  font-size: 11px;

  font-weight: 800;

  letter-spacing: 2px;

  text-transform: uppercase;
}

.partnership-message {
  width: min(1100px, 100%);

  margin: 90px auto 0;

  padding: 45px;

  display: flex;
  align-items: center;
  justify-content: space-between;

  gap: 50px;

  border-top: 1px solid rgba(255, 255, 255, 0.2);
}

.partnership-message span {
  color: #ffb21b;

  font-size: 11px;

  letter-spacing: 2px;
}

.partnership-message h3 {
  margin: 8px 0 0;

  font-size: 32px;
}

.partnership-message p {
  max-width: 500px;

  color: #bdc9c9;

  line-height: 1.8;
}

@media (max-width: 1050px) {
  .partners-container {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 650px) {
  .partnership-section {
    padding: 80px 6%;
  }

  .partners-container {
    grid-template-columns: 1fr;
  }

  .partnership-message {
    flex-direction: column;
    align-items: flex-start;

    padding: 30px 0;
  }
}
</style>