<template>
  <section id="home" class="hero">

    <div class="hero-overlay"></div>

    <div class="hero-container">

      <div class="hero-content">

        <p class="hero-small">
          THE CCS CORE PRACTICES THAT BUILD BRIDGES BETWEEN GAPS
        </p>

        <h1>
          Learning HTML<br />
          CSS is a lot more challenging<br /> 
          than it used to be. Responsive web design<br />
          more layers of complexity<br />
          SHARE
        </h1>

        <p class="hero-tagline">
          different people, <strong>ONE</strong> goal
        </p>

        <RouterLink to="/#programs" class="hero-button">
          Welcome to World Of technology
        </RouterLink>

      </div>

      <div class="hero-logo">
        <img
          src="/images/ccs-logo.png"
          alt="CCS Logo"
        />
      </div>

    </div>

    <div class="hero-scroll">
      <span>EXPLORE</span>
      <div class="scroll-line"></div>
    </div>

  </section>
</template>

<style scoped>
.hero {
  position: relative;

  min-height: 100vh;

  overflow: hidden;

  display: flex;
  align-items: center;

  background:
    linear-gradient(
      110deg,
      #062d30 0%,
      #0b393b 48%,
      #102f30 100%
    );
}

.hero::before {
  content: "";

  position: absolute;
  inset: 0;

  background-image: url("/images/hero-bg.jpg");
  background-size: cover;
  background-position: center right;

  opacity: 0.3;
}



.hero-container {
  position: relative;
  z-index: 2;

  width: min(1400px, 90%);
  margin: 0 auto;

  display: flex;
  align-items: center;
  justify-content: space-between;
}

.hero-content {
  max-width: 650px;
  padding-top: 70px;
}

.hero-small {
  margin-bottom: 20px;

  color: #c7c7c7;

  font-size: 15px;
  font-weight: 600;
  letter-spacing: 0.5px;
}

.hero h1 {
  margin: 0;

  color: #ffffff;

  font-size: clamp(48px, 6vw, 82px);
  line-height: 0.93;

  font-weight: 800;
  letter-spacing: -2px;
}

.hero-tagline {
  margin-top: 28px;

  color: #ffb21b;

  font-size: clamp(22px, 2.4vw, 32px);
}

.hero-tagline strong {
  font-weight: 700;
}

.hero-button {
  display: inline-block;

  margin-top: 45px;
  padding: 17px 35px;

  border-radius: 5px;

  background: #05ec3f;
  color: #083337;

  text-decoration: none;

  font-size: 17px;
  font-weight: 700;

  transition: 0.3s ease;
}

.hero-button:hover {
  background: #ffffff;
  transform: translateY(-4px);
  box-shadow: 0 12px 25px rgba(0, 0, 0, 0.25);
}

.hero-logo {
  width: 480px;
  height: 480px;

  display: flex;
  align-items: center;
  justify-content: center;

  opacity: 0.9;
}

.hero-logo img {
  width: 100%;
  height: 100%;
  object-fit: contain;
  filter: drop-shadow(0 15px 35px rgba(0, 0, 0, 0.3));
}

.hero-scroll {
  position: absolute;
  z-index: 5;

  bottom: 30px;
  left: 50%;

  transform: translateX(-50%);

  display: flex;
  flex-direction: column;
  align-items: center;

  color: #ffffff;
}

.hero-scroll span {
  font-size: 10px;
  letter-spacing: 2px;
  opacity: 0.7;
}

.scroll-line {
  width: 1px;
  height: 35px;

  margin-top: 8px;

  background: #ffb21b;
}

@media (max-width: 900px) {
  .hero-container {
    justify-content: center;
  }

  .hero-content {
    text-align: center;
  }

  .hero-logo {
    display: none;
  }

  .hero h1 {
    font-size: clamp(45px, 10vw, 70px);
  }
}

@media (max-width: 500px) {
  .hero {
    min-height: 100svh;
  }

  .hero-container {
    width: 88%;
  }

  .hero-content {
    padding-top: 50px;
  }

  .hero-small {
    font-size: 12px;
    line-height: 1.5;
  }

  .hero h1 {
    font-size: 45px;
  }

  .hero-tagline {
    font-size: 20px;
  }

  .hero-button {
    margin-top: 30px;
    padding: 15px 25px;
    font-size: 15px;
  }
}
</style>