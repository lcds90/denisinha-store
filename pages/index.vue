
<template>
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
</template>

<script>

export default {
  layout: 'home',
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
