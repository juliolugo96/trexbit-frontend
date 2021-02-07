<template>
  <div>
    <section>
      <div class="container column is-10">
        <nuxt />
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          title: 'Home',
          icon: 'home',
          to: { name: 'index' },
        },
      ],
    }
  },
}
</script>
<style lang="sass">
body
  background-image: linear-gradient(315deg, #faaca8 10%, #ddd6f3 33%) !important
  height: 100vh
</style>
