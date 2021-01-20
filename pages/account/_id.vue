<template>
  <div class="detail-page">
    <div v-if="$route.path.endsWith('standalone-nested')">standalone</div>
    <div v-else class="container">
      <div class="row py-2">
        <div class="col">
          <h1 class="title">Main Page ~ Account Detail (id: {{ id }})</h1>
        </div>
      </div>

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
        <button @click="toggleBetweenComponents" style="margin: 1rem 0">
          Replace nuxt-child by the Standalone component
        </button>

        <ul class="nav nav-tabs">
          <li class="nav-item">
            <nuxt-link tag="a" class="nav-link active" :to="`/en/account/123/nested-a`">Nested A</nuxt-link>
          </li>
          <li class="nav-item">
            <nuxt-link tag="a" class="nav-link active" :to="`/en/account/123/nested-b`">Nested B</nuxt-link>
          </li>
        </ul>
        <div class="tab-content" id="myTabContent">
          <component :is="nuxtChildOrStandaloneComponent"></component>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AccountIdMainPage',
  components: {
    ExampleStandalone: () => import('~/components/ExampleStandalone.vue'),
  },
  data() {
    return {
      id: null,
      nuxtChildOrStandaloneComponent: 'nuxt-child',
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
  methods: {
    toggleBetweenComponents() {
      if (this.nuxtChildOrStandaloneComponent === 'nuxt-child') {
        this.nuxtChildOrStandaloneComponent = 'example-standalone'
      } else {
        this.nuxtChildOrStandaloneComponent = 'nuxt-child'
      }
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
