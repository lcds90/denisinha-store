
<template>
  <div class="layout">
    <Header />
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
  grid: 0.5fr 1fr 0.1fr / 1fr;
  grid-template-areas:
    "header"
    "main"
    "footer";
}

.main {
  grid-area: main;
  background-color: var(--background);
}

@media screen and (min-width: 768px) {
  .layout {
    grid: 0.35fr 2fr 0.15fr / 1fr;
    grid-template-areas:
      "header"
      "main"
      "footer";
  }
}

</style>
