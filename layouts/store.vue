<template>
  <div class="layout-store">
    <Header />
    <aside
      class="aside"
    >
      <Nuxt />
    </aside>
    <main
      class="main"
    >
      <Nuxt />
    </main>
    <Footer />
  </div>
</template>

<style>

.layout-store {
  width: 100vw;
  max-width: 100%;
  min-height: 100vh;
  display: grid;
  grid: 0.5fr 0.15fr 1fr / 1fr;
  grid-template-areas:
    "header"
    "aside"
    "main";
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
  .layout-store {
    grid: 0.35fr 2fr 0.15fr / 0.15fr 1fr;
    grid-template-areas:
      "header header"
      "aside main"
      "aside main";
  }
}

</style>
