<router>
{
  alias: [
    '/:locale/account/:id/external-standalone-nested',
  ]
}
</router>

<template>
  <div class="container">
    not even in the folder here
  </div>
</template>

<script>
export default {
  watch: {
    $route: {
      handler() {
        this.id = this.$route.params.id
      },
      immediate: true,
    },
  },

  mounted() {
    console.warn('mounted: external standalone mounted')
  },
}
</script>
