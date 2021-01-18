<template>
  <div class="detail-page">
    <div class="container">
      <div class="row py-2">
        <div class="col">
          <h1 class="title">
            Account Detail (id: {{ id }})
          </h1>
        </div>
      </div>
      <div class="row py-2">
        <div class="col">
          <nuxt-link tag="a" class="btn btn-danger" :to="`/en/account/123/standalone`">Standalone Page</nuxt-link>
        </div>
      </div>
      <div>
        <ul class="nav nav-tabs">
          <li class="nav-item">
            <nuxt-link tag="a" class="nav-link active" :to="`/en/account/123/nested-a`">Nested A</nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link tag="a" class="nav-link active" :to="`/en/account/123/nested-b`">Nested B</nuxt-link>
          </li>
        </ul>
        <div class="tab-content" id="myTabContent">
          <NuxtChild/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  components: {},
  data() {
    return {
      id: null
    }
  },
  watch: {
    $route: {
      handler() {
        this.id = this.$route.params.id
      },
      immediate: true
    }
  },

  mounted() {
    console.warn('mounted: Detail')
  }
}
</script>

<style scoped>
.detail-page {
    background-color: cornflowerblue;
    height: 100%;
}
</style>
