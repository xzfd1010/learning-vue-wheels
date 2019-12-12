<template>
  <button class="l-button" :disabled="disabled" :class="[`icon-${iconPosition}`]"
          @click="$emit('click')">
    <icon class="icon" v-if="icon && !loading" :name="icon"></icon>
    <icon class="icon loading" v-if="loading" name="loading"></icon>
    <span class="content">
      <slot></slot>
    </span>
  </button>
</template>

<script>
import Icon from './icon'

export default {
  name: 'LButton',
  components: { Icon },
  props: {
    icon: {
      type: String
    },
    disabled: {
      type: Boolean,
      default: false
    },
    iconPosition: {
      type: String,
      default: 'left',
      validator (value) {
        return value === 'left' || value === 'right'
      }
    },
    loading: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style scoped lang="scss">
  @import "styles/var";
  .l-button {
    font-size: $font-size;
    height: $button-height;
    background: $button-bg;
    border-radius: $border-radius;
    border: 1px solid $border-color;
    padding: 0 1em;
    color: $color;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    &:hover {
      border-color: $border-color-hover;
    }
    &:active {
      background-color: $button-active-bg;
    }
    &:focus {
      outline: none;
    }
    &:disabled {
      color: $disabled-color; // graytext是浏览器的默认样式，#d3d3d3
      cursor: not-allowed;
      background-image: none;
      border-color: $disabled-border-color;
    }
    > .icon {
      order: 1;
      margin-right: .1em;
    }
    > .content {
      order: 2;
    }
    &.icon-right {
      > .icon {
        order: 2;
        margin-left: .1em;
        margin-right: 0;
      }
      > .content {
        order: 1;
      }
    }
    .loading {
      animation: spin 1.5s infinite linear;
    }
  }
</style>
