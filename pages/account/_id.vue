<template>
  <div class="detail-page">
    <div v-if="$route.path.endsWith('standalone-nested')">standalone</div>
    <div v-else class="container">
      <div class="row py-2">
        <div class="col">
          <h1 class="title">Main Page ~ Account Detail (id: {{ id }})</h1>
        </div>
      </div>
      <!-- v-if="$route.path.endsWith('standalone')" -->
      <div class="row py-2">
        <div class="col">
          <nuxt-link tag="a" class="btn btn-danger" :to="`/en/account/123/standalone-nested`">
            "main page" Standalone Page
          </nuxt-link>
          <nuxt-link tag="a" class="btn btn-danger" :to="`/en/account/123/external-standalone-nested`">
            Real external Standalone Page ?
          </nuxt-link>
        </div>
      </div>
      <div>
        <!-- v-else -->
        <ul class="nav nav-tabs">
          <li class="nav-item">
            <nuxt-link tag="a" class="nav-link active" :to="`/en/account/123/nested-a`">Nested A</nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link tag="a" class="nav-link active" :to="`/en/account/123/nested-b`">Nested B</nuxt-link>
          </li>
        </ul>
        <div class="tab-content" id="myTabContent">
          <nuxt-child></nuxt-child>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AccountIdMainPage',
  data() {
    return {
      id: null,
    }
  },
  watch: {
    $route: {
      handler() {
        this.id = this.$route.params.id
      },
      immediate: true,
    },
  },

  mounted() {
    console.warn('mounted: Detail')
  },
}
</script>

<style scoped>
.detail-page {
    background-color: cornflowerblue;
    height: 100%;
}
</style>
