<template>
  <div class="layout-menu-container">
    <AppSubmenu :items="model" class="layout-menu" :root="true" @menuitem-click="onMenuItemClick" />
    <a href="https://www.primefaces.org/primeblocks-vue" class="block mt-3">
      <img alt="primeblocks" :src="bannerImage()" class="w-full">
    </a>
  </div>
</template>

<script lang="ts">
import AppSubmenu from './AppSubmenu.vue'

export default {
  components: {
    AppSubmenu
  },
  props: {
    model: {
      type: Array,
      default: () => ([])
    }
  },
  emits: ['menuitem-click'],
  computed: {
    darkTheme () {
      return this.$appState.darkTheme
    }
  },
  methods: {
    onMenuItemClick (event) {
      this.$emit('menuitem-click', event)
    },
    bannerImage () {
      return this.$appState.darkTheme ? '/images/banner-primeblocks-dark.png' : '/images/banner-primeblocks.png'
    }
  }
}
</script>

<style scoped>

</style>
