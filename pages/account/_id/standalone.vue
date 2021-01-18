<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <h1 class="title">
          Standalone (id: {{ id }})
        </h1>
        <p>
          This should not be rendered inside parent!
        </p>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  components: {
  },
  data () {
    return {
      id: null
    }
  },
  watch: {
    $route: {
      handler () {
        this.id = this.$route.params.id
      },
      immediate: true
    }
  },

  mounted() {
    console.warn('mounted: Standalone')
  }
}
</script>
