<script>
import ColoredItem from './ColoredItem.vue'

export default {
  props: ['text', 'index', 'type', 'marker'],
  components: {
    ColoredItem,
  },
};
</script>

<template>
<div>
  <div class="marker-text-colored__summary">
    <slot name="summary"></slot>
  </div>
  <ColoredItem :type="type" :marker="marker" @select="$emit('select', index)">
    <slot>
      {{text}}
    </slot>
  </ColoredItem>  
</div> 
</template>

<style lang="less">
.marker-text-colored {
  &__summary {
    font-size: @font-sm; 
    padding-bottom: @indent-xs; 
    color: @gray-dark; 
  }
}
</style>
