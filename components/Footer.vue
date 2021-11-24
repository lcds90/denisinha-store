<template>
  <footer class="footer">
    <article>
      Feito com ✰⋆💖✨ por
      <button>
        👨🏽‍💻 LL Developments 👨🏽‍💻
      </button>
    </article>
    <article>
      <a href="https://www.instagram.com/deniseilustra/" target="_blank">
        Instagram
      </a>
      <a href="mailto:oideniseilustra@gmail.com">
        <font-awesome-icon
          :icon="['fas', 'envelope']"
        />
        Enviar e-mail para a denisinha

      </a>
    </article>
  </footer>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<style scoped>

.footer {
  grid-area: footer;
  background-color: var(--footer);
  display: grid;
  place-items: center;
  color: white;
  border-top: 0.5px solid black;
}

button {
  display: grid;
  padding: 0.5px;
  border-radius: 5px;
  border: 0;
}
</style>
