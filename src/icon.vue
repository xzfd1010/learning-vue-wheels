<template>
  <svg class="l-icon">
    <use :xlink:href="`#icon-${name}`"></use>
  </svg>
</template>

<script>
import './svg'

export default {
  name: 'icon',
  props: ['name']
}
</script>

<style lang="scss" scoped>
  .l-icon {
    width: 1em;
    height: 1em;
  }
</style>
