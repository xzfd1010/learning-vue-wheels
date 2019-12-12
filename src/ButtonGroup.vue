<template>
  <div class="l-button-group">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'ButtonGroup',
  mounted () {
    for (let node of this.$el.children) {
      if (node.nodeName.toLowerCase() !== 'button') {
        console.warn(`button-group的内部应该都是button，但你写的是${node.nodeName.toLowerCase()}`)
      }
    }
  }
}
</script>

<style scoped lang="scss">
  @import "styles/var";
  .l-button-group {
    display: inline-flex;
    vertical-align: middle;
    > .l-button {
      border-radius: 0;
      &:not(:first-child) {
        margin-left: -1px;
      }
      &:first-child {
        border-top-left-radius: $border-radius;
        border-bottom-left-radius: $border-radius;
      }
      &:last-child {
        border-top-right-radius: $border-radius;
        border-bottom-right-radius: $border-radius;
      }
      &:hover {
        position: relative;
        z-index: 1;
      }
    }
  }
</style>
