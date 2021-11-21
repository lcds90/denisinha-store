
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
      aside
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
      main
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
  grid: 0.35fr 2fr 0.15fr / 0.15fr 1fr;
  grid-template-areas:
    "header header"
    "aside main"
    "footer footer";
}

.aside {
  grid-area: aside;
  background-color: var(--primary);
}

.main {
  grid-area: main;
  background-color: var(--secondary);
}

</style>
