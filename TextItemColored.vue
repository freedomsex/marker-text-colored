<script>
export default {
  props: ['text', 'index', 'type', 'marker'],
  computed: {
    status() {
      let values = {
        'success': 1,
        'info': 2,
        'warning': 4,
        'danger': 8,
      };
      return values[this.type] || 0;
    },
    value() {
      return this.marker !== undefined ? this.marker : this.status;
    },
    colored() {
      return {
        success: this.value === 1,
        info: this.value === 2,
        warning: this.value === 4,
        danger: this.value === 8,
        skiped: !this.value,
      };
    },
  },
};
</script>

<template>
  <div class="text-item-colored" :class="colored" @click="$emit('select', index)">
    <slot>
      {{text}}
    </slot>
  </div>
</template>

<style lang="less">
.text-item-colored {
  color: @black;
  font-size: @font-md;
  margin-bottom: @indent-xs;
  padding: @indent-sm;
  border-style: solid;
  border-width: 0 0 0 @border-xl;
  background: @light;
  position: relative;

  &.success {
    border-color: @green;
  }
  &.info {
    border-color: @violet;
  }
  &.warning {
    border-color: @orange-light;
  }
  &.danger {
    border-color: @red;
  }
  &.skiped {
    border-color: @gray-light;
  }
}
</style>
