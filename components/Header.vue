<template>
  <header class="header">
    <div class="line" />
    <div class="logo">
      <img src="~/assets/img/logo.png" alt="">
    </div>
    <nav>
      <div class="links">
        home
      </div>
      <div class="links">
        portfolio
      </div>
      <div class="links">
        itens
      </div>
      <div class="links">
        contato
      </div>
    </nav>
    <nav>
      <span class="user" />
      <div class="links">
        Entrar
      </div> <!-- Quando logado, minha conta -->
      <div class="links">
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
      gsap.from('.links', { rotation: 860, y: -300, duration: 1, stagger: 1 })
        .fromTo('.links', { fontSize: '1.6rem', filter: 'brightness(1.5)', duration: 1, stagger: 1 }, { fontSize: '2.5rem', filter: 'brightness(1)', stagger: 1 }, '-=5')
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
  background-color: var(--header);
  display: grid;
  grid: 1fr / 1fr 2fr 1fr;
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

nav {
  display: grid;
  grid-template-rows: 1fr;
  grid-auto-flow: column;
  grid-auto-columns: 1fr;
  gap: 1rem;
}

.links {
  font-size: 2.5rem;
  font-weight: 200;
  color: blue;
  padding: 5px;
  background-color: var(--background);
  text-align: center;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);
  border-radius: 5px;
}

.logo img {
  width: 10rem;
}
</style>
