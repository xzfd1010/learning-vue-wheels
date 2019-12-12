<template>
  <div id="app">
    <l-button-group>
      <l-button :loading="true" icon-position="right">测试</l-button>
      <l-button>哈哈</l-button>
    </l-button-group>
  </div>
</template>

<script>
import LButton from './Button'
import LButtonGroup from './ButtonGroup'

export default {
  name: 'app',
  components: {
    LButton,
    LButtonGroup
  }
}
</script>

<style>

</style>
