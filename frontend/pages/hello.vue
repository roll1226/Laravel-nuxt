<template>
  <div>
    <h1>{{ data }}</h1>
  </div>
</template>

<script>
export default {
  layout: 'pagebase',

  async asyncData({ app }) {
    const data = await app.$axios.$get('http://localhost:8000/api/hello')
    return { data }
  }
}
</script>
