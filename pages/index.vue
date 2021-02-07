<template>
  <section class="section">
    <h1 class="has-text-centered title is-1">Hello, Trexbit</h1>
    <users-table />
  </section>
</template>

<script>
import UsersTable from '@/components/UsersTable'

export default {
  name: 'HomePage',
  components: {
    UsersTable,
  },
}
</script>
