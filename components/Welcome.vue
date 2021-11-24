<template>
  <section>
    <article class="logoContainer">
      <div class="logo">
        <img src="~/assets/img/banner.jpg" alt="">
      </div>
    </article>
    <article class="welcome">
      Olá, seja bem vindo.
    </article>
  </section>
</template>

<script>
export default {
  name: 'Welcome',
  mounted () {
    this.logoAnimation()
  },
  methods: {

    logoAnimation () {
      // const gsap = this.$gsap
      const tl = this.$gsap.timeline({ ease: 'linear', duration: 2 })
      // gsap.from('.logo', { rotation: 180, x: -500, duration: 1.5, ease: 'bounce' })
      tl
        .to('.welcome', { x: 5, scale: 1, color: 'black' })
        .from('.welcome', { x: 5 })
        .to('.welcome', { scale: 1.05, duration: 3, ease: 'bounce', color: 'white' })
        .fromTo('.welcome', { delay: 5, filter: 'brightness(1.005)', scale: 1.05, duration: 3, ease: 'circ' },
          { x: 5, scale: 1.05, filter: 'none', color: 'black' }
        )
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
}

.logo img {
  width: 30rem;
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

@media screen and (min-width: 768px) {
  section {
    grid: 1fr / 1fr 1fr;
  }

  .logo img {
    width: 40rem;
  }
}

</style>
