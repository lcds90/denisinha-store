<template>
  <header class="header">
    <div class="line" />
    <div class="logo">
      <img src="~/assets/img/logo.png" alt="">
    </div>
    <nav class="sites-links">
      <div class="links home">
        home
      </div>
      <div class="links portfolio">
        portfolio
      </div>
      <div class="links store">
        loja
      </div>
    </nav>
    <nav class="user-links">
      <div class="links account">
        Entrar
      </div> <!-- Quando logado, minha conta -->
      <div class="links cart">
        Carrinho
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'Header',
  mounted () {
    this.logoAnimation()
    this.iconsAnimation()
    this.borderAnimation()
  },
  methods: {
    logoAnimation () {
      // const gsap = this.$gsap
      const tl = this.$gsap.timeline({ ease: 'linear', duration: 2, repeat: -1 })
      // gsap.from('.logo', { rotation: 180, x: -500, duration: 1.5, ease: 'bounce' })
      tl
        .to('.logo img', { x: 5, scale: 1 })
        .from('.logo img', { x: 5 })
        .to('.logo img', { x: 5, scale: 1.05, duration: 3, ease: 'bounce' })
        .fromTo('.logo img', { delay: 5, filter: 'brightness(1.005)', x: 5, scale: 1.05, duration: 3, ease: 'circ' },
          { x: 5, scale: 1.05, filter: 'none' }
        )
    },
    iconsAnimation () {
      const gsap = this.$gsap.timeline()
      gsap.from('.links', { rotation: 860, y: -300, duration: 1, stagger: 0.35 })
        .fromTo('.links', { fontSize: '0.6rem', filter: 'brightness(1.5)', duration: 1, stagger: 0.15 }, { fontSize: '1.6rem', filter: 'brightness(1)', stagger: 1 }, '-=5')
    },
    borderAnimation () {
      const gsap = this.$gsap.timeline()
      gsap.fromTo('.line', { opacity: 0, width: '0%', duration: 2 }, { opacity: 1, width: '100%', duration: 4, delay: 5 })
    }
  }
}
</script>

<style scoped>
.header {
  max-width: 100%;
  grid-area: header;
  background-color: var(--primary);
  display: grid;
  grid: 1fr / 1fr 1fr;
  place-items: center;
  position: relative;
}

.line {
  position: absolute;
  width: 100%;
  height: 1%;
  background: white;
  bottom: 0;
}

.sites-links {
  display: grid;
  grid-template-rows: 1fr 1fr;
  grid-template-columns: 1fr 1fr;
  gap: 1rem;
  padding: 1rem;
}

.user-links {
  display: grid;
  grid-template-rows: 1fr 1fr;
  grid-template-columns: 1fr;
  gap: 1rem;
  padding: 1rem;
}

.user {
  grid-column: span 2;
}

.links {
  font-weight: 800;
  color: white;
  padding: 5px;
  text-align: center;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
  border-radius: 5px;
  width: 100%;
  height: 100%;
  margin: auto;
  text-transform: uppercase;
  transition: background 0.5s ease-out, color 1s ease-in;
  display: grid;
  place-items: center;
}

.links:hover {
  background-color: var(--background);
  color: var(--secondary);
  cursor: pointer;
}

.home {
  background-color: blueviolet;
}

.portfolio {
  background-color: blueviolet;
}

.store {
  background-color: blueviolet;
  grid-column: span 2;
}

.account {
  background-color: lightblue;
}

.cart {
  background-color: orange;
}

.logo {
  grid-column: span 2;
}

.logo img {
  width: 10rem;
}

@media screen and (min-width: 768px) {
  .header {
    grid: 1fr / 1fr 2fr 1fr;
  }

  .logo {
    grid-column: span 1;
  }

  .sites-links,
  .user-links {
    grid-template-rows: 1fr;
    grid-auto-flow: column;
    grid-auto-columns: 1fr;
    gap: 1rem;
    padding: 1.5rem;
    width: 100%;
    height: 75%;
  }
}

</style>
