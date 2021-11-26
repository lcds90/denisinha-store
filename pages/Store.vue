
<template>
  <div class="layout">
    <Header />
    <aside
      v-gsap.from="{
        x: -150,
        duration: 1.5
      }"
      class="aside"
    >
      <section>categoria 1</section>
      <section>categoria 2</section>
      <section>categoria 3</section>
    </aside>
    <main
      v-gsap.from="{
        scale: 0.95,
        opacity: 0,
        duration: 1,
        ease: 'bounce'
      }"
      class="main"
    >
      <Welcome />
    </main>
    <Footer />
  </div>
</template>

<script>

export default {
  name: 'Home',
  data () {
    return {
      show: true,
      title: 'Loja da denisinha!'
    }
  },
  head () {
    return {
      title: this.title,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: 'description',
          name: 'description',
          content: 'My custom description'
        }
      ]
    }
  }
}
</script>

<style>

.layout {
  width: 100vw;
  max-width: 100%;
  min-height: 100vh;
  display: grid;
  grid: 0.5fr 0.15fr 1fr 0.1fr / 1fr;
  grid-template-areas:
    "header"
    "aside"
    "main"
    "footer";
}

.aside {
  grid-area: aside;
  background-color: var(--black);
}

.aside > section {
  background-color: var(--primary);
  margin: 5px;
}

.main {
  grid-area: main;
  background-color: var(--background);
}

@media screen and (min-width: 768px) {
  .layout {
    grid: 0.35fr 2fr 0.15fr / 0.15fr 1fr;
    grid-template-areas:
      "header header"
      "aside main"
      "aside footer";
  }
}

</style>
