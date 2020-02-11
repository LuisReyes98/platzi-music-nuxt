<template lang="pug">
  div
    pm-header
    nuxt
    pm-footer
</template>

<script>
import PmHeader from '~/components/Header.vue'
import PmFooter from '~/components/Footer.vue'

export default {
  name: 'Layout',
  components: { 'pm-header': PmHeader, PmFooter }
}
</script>

<style>
</style>
