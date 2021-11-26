<template>
  <footer class="footer">
    <article class="footer-links">
      <a class="instagram" href="https://www.instagram.com/deniseilustra/" target="_blank" rel="noopener noreferrer">
        <font-awesome-icon
          :icon="['fab', 'instagram']"
        />
        Instagram
      </a>
      <a class="email" href="mailto:oideniseilustra@gmail.com" rel="noopener noreferrer">
        <font-awesome-icon
          :icon="['fas', 'envelope']"
        />
        Enviar e-mail
      </a>
      <a class="apoia-se" href="https://apoia.se/deniseilustra" target="_blank" rel="noopener noreferrer">
        <font-awesome-icon
          :icon="['fas', 'star']"
        />
        Apoia.se
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
  background-color: var(--black);
  color: white;
  display: grid;
  position: relative;
  border-left: 5px solid var(--background);
}

.footer-links {
  position: relative;
  height: 100%;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(50px, 1fr));
  place-items: center;
  gap: 1rem;
  padding: 0 5px;
}

.footer-links a {
  margin: 5px;
  color: white;
  background-color: var(--secondary);
  text-decoration: none;
  border-radius: 5px;
  display: grid;
  place-items: center;
  transition: background 1.5s ease-out, color 0.25s ease-in;
  width: 100%;
  font-size: 1.25rem;
}

.footer-links a:hover {
  color: black;
  background: var(--primary);
  cursor: pointer;
}

@media screen and (min-width: 768px) {
  .footer-links a {
    padding: 5px;
    width: 60%;
  }
}

</style>
