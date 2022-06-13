<template>
  <header class="header">
    <div class="line" />
    <div class="logo">
      <span class="speak" />
      <img src="~/assets/img/logo.png" alt="">
    </div>
    <nav class="sites-links">
      <div class="links home">
        <NuxtLink to="/">
          <font-awesome-icon :icon="['fas', 'home']" />
          Home
        </NuxtLink>
      </div>
      <div class="links portfolio">
        <NuxtLink to="/">
          <font-awesome-icon :icon="['fas', 'grin-stars']" />
          portfolio
        </NuxtLink>
      </div>
      <div class="links store">
        <NuxtLink to="/store">
          <font-awesome-icon :icon="['fas', 'shopping-bag']" />
          Loja
        </NuxtLink>
      </div>
    </nav>
    <nav class="user-links">
      <div class="links account">
        <NuxtLink to="/">
          <font-awesome-icon :icon="['fas', 'user']" />
          Entrar
        </NuxtLink>
      </div>
      <!-- Quando logado, minha conta -->
      <div class="links cart">
        <NuxtLink to="/">
          <font-awesome-icon :icon="['fas', 'shopping-cart']" />
          Carrinho
        </NuxtLink>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  mounted () {
    this.logoAnimation()
    this.iconsAnimation()
    this.borderAnimation()
    setTimeout(() => this.denisinhaSpeechAnimation(), 200)
  },
  methods: {
    logoAnimation () {
      const tl = this.$gsap.timeline({
        ease: 'linear',
        duration: 2,
        repeat: -1,
        clearProps: 'all'
      })
      tl.to('.logo img', { x: 5, scale: 1 })
        .from('.logo img', { x: 5 })
        .to('.logo img', { x: 5, scale: 1.05, duration: 3, ease: 'bounce' })
        .fromTo(
          '.logo img',
          {
            delay: 5,
            filter: 'brightness(1.005)',
            x: 5,
            scale: 1.05,
            duration: 3,
            ease: 'circ'
          },
          { x: 5, scale: 1.05, filter: 'none' }
        )
    },
    iconsAnimation () {
      const gsap = this.$gsap
      gsap.from('.links', {
        x: -15,
        duration: 2,
        rotation: 0.15,
        filter: 'hue-rotate(25deg)',
        stagger: 0.25,
        clearProps: 'all'
      })
      gsap.from('.header .logo img', {
        delay: 1,
        opacity: 0,
        duration: 2
      })
    },
    borderAnimation () {
      const gsap = this.$gsap.timeline({ clearProps: 'all' })
      gsap.fromTo(
        '.line',
        { opacity: 0, width: '0%', duration: 2 },
        { opacity: 1, width: '100%', duration: 4, delay: 5 }
      )
    },
    denisinhaSpeechAnimation () {
      const gsap = this.$gsap.timeline({
        clearProps: 'all',
        duration: 5,
        ease: 'bounce'
      })
      const el = '.speak'
      const textConfig = {
        delay: 1,
        duration: 2,
        ease: 'none'
      }
      gsap
        .to(el, { opacity: 1 })
        .to(el, {
          ...textConfig,
          text: { speed: 0.75, value: 'Olá, sou a Denisinha' }
        })
        .to(el, {
          ...textConfig,
          text: { speed: 0.75, value: 'Irei te auxiliar em sua jornada pelo nosso site! :)' }
        })
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
  border-left: 0.5px solid grey;
  width: 100%;
}

.user {
  grid-column: span 2;
}

.links {
  font-weight: 800;
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
  cursor: pointer;
}

.links a {
  width: 100%;
  height: 100%;
  display: grid;
  place-items: center;
  color: white;
  text-decoration: none;
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
  transform: translateX(9rem);
  grid-column: span 2;
}

.logo img {
  width: 10rem;
}

span.speak {
  position: fixed;
  top: 0.5rem;
  left: -20rem;
  width: 20rem;
  display: grid;
  place-items: center;
  font-size: 1rem;
  background: white;
  border-radius: 2px;
  padding: 0.5px 15px 15px 10px;
  opacity: 0;
  clip-path: polygon(0% 0%, 95% 0, 95% 67%, 100% 76%, 87% 76%, 0% 75%);
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

/* iPhone specific */
@media screen and (min-width: 320px) and (max-height: 568px) {
  .logo img {
    width: 7rem;
  }
}

/* Galaxy Fold */
@media screen and (max-width: 320px) and (min-height: 653px) {
  .header {
    grid: 1fr / 1fr;
  }

  .logo {
    grid-column: span 1;
  }

  .user-links {
    border: none;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: 1fr;
  }

  .sites-links {
    padding: 0.25rem;
  }

  .logo img {
    width: 8rem;
  }
}
</style>
