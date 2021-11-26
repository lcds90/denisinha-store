<template>
  <div class="layout">
    <Header />
    <Nuxt />
    <Footer />
  </div>
</template>

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
