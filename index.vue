<script>
export default {
  props: ['text', 'marker', 'color'],
  data() {
    return {
      option: null,
    };
  },
  computed: {
    status() {
      let values = {
        'success': 1,
        'info': 2,
        'warning': 4,
        'danger': 8,
      };
      return values[this.color] || 0;
    },
    value() {
      return this.marker !== null ? this.marker : this.status;
    },
    colored() {
      return {
        closed: this.value === 1,
        virted: this.value === 2,
        locked: this.value === 4,
        banned: this.value === 8,
        skiped: !this.value,
      };
    },
  },
};
</script>

<template>
  <div class="marker-text-colored" :class="colored" @click="$emit('select')">
    <slot>
      {{text}}
    </slot>
  </div>
</template>

<style lang="less">
// @import "~assets/css/_imports.less";
.marker-text-colored {
  color: @dark;
  font-size: @font-md;
  margin-bottom: @indent-xs;
  padding: @indent-sm;
  border-style: solid;
  border-width: 0 0 0 @border-xl;
  background: @light;
  position: relative;

  &.closed {
    border-color: @green;
  }
  &.virted {
    border-color: @violet;
  }
  &.locked {
    border-color: @orange-light;
  }
  &.banned {
    border-color: @red;
  }
  &.skiped {
    border-color: @gray;
  }
}
</style>
