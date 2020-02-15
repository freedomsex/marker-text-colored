<script>
import TextItemColored from './TextItemColored.vue'

export default {
  props: ['text', 'index', 'type', 'marker'],
  components: {
    TextItemColored,
  },
};
</script>

<template>
<div class="marker-text-colored">
  <div class="marker-text-colored__summary">
    <slot name="summary"></slot>
  </div>
  <TextItemColored :type="type" :marker="marker" @select="$emit('select', index)">
    <slot>
      {{text}}
    </slot>
  </TextItemColored>  
</div> 
</template>

<style lang="less">
.marker-text-colored {
  margin-bottom: @indent-sm;

  &__summary {
    font-size: @font-sm; 
    padding-bottom: @indent-xs; 
    color: @gray-dark; 
  }
}
</style>
