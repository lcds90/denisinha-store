<template>
  <section>
    <article class="logoContainer">
      <div class="logo">
        <img src="~/assets/img/banner.jpg" alt="">
      </div>
    </article>
    <article class="welcome">
      <h1>Olá, seja bem vindo.</h1>
      <p>Sou Denise Bueno, ilustradora e animadora.</p>
      <p>Residente em São Paulo / SP</p>
      <p>
        Também sou tatuadora no
        <a href="https://www.instagram.com/eclipseartestudio/" target="_blank" rel="noopener noreferrer">
          Eclipse Arte Studio
        </a>
      </p>
    </article>
    <article class="credits">
      Feito com ✰⋆💖✨ por
      👨🏽‍💻 LL Developments 👨🏽‍💻
    </article>
  </section>
</template>

<script>
export default {
  name: 'Welcome',
  mounted () {
    this.logoAnimation()
    this.creditAnimation()
  },
  methods: {
    logoAnimation () {
      const tl = this.$gsap.timeline({ ease: 'linear', duration: 2 })
      tl
        .to('.welcome', { x: 5, scale: 1, color: 'black' })
        .from('.welcome', { x: 5 })
        .to('.welcome', { scale: 1.05, duration: 3, ease: 'bounce', color: 'white' })
        .fromTo('.welcome', { delay: 5, filter: 'brightness(1.005)', scale: 1.05, duration: 3, ease: 'circ' },
          { x: 5, scale: 1.05, filter: 'none', color: 'black' }
        )
    },
    creditAnimation () {
      const tl = this.$gsap.timeline()
      tl
        .from('.credits', { x: -3000, duration: 5 })
        .to('.credits', { y: -10, duration: 1 })
        .to('.credits', { y: 25, duration: 2.5, ease: 'bounce' })
        .to('.credits', { y: 0, duration: 5, delay: 3 })
    }
  }
}
</script>

<style scoped>

section {
  display: grid;
  grid: 1fr 1fr / 1fr;
  height: 100%;
  width: 100%;
  place-items: center;
  position: relative;
  overflow: hidden;
}

.logo img {
  width: 25rem;
  height: auto;
  border-radius: 15px;
  box-shadow: 0 5px 5px rgba(0, 0, 0, 0.25);
}

.logoContainer {
  background-color: #eeb17cb4;
  width: 90%;
  height: 45%;
  display: grid;
  place-items: center;
  border-radius: 50px 5px 25px 5px;
}

.credits {
  background: grey;
  top: -16.5px;
  right: 0;
  border-bottom: 2px solid white;
  border-left: 2px solid white;
  border-radius: 0 0 0 15px;
  padding: 5px;
  font-size: 1rem;
  position: absolute;
  transition: top 0.5s ease;
}

.credits:hover {
  top: 0;
}

.welcome {
  padding: 15px;
}

@media screen and (min-width: 768px) {
  section {
    grid: 1fr / 1fr 1fr;
  }

  .logo img {
    width: 40rem;
  }
}

</style>
