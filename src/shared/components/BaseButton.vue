<template>
  <button
    class="button"
    :class="{ disabled: props.disabled }"
    :disabled="props.disabled"
    @click="emit('handleClick')"
  >
    <slot></slot>
  </button>
</template>

<script setup lang="ts">
const props = defineProps<{
  disabled?: boolean
}>()

const emit = defineEmits(['handleClick'])
</script>

<style lang="scss" scoped>
.button {
  background-color: blue;
  padding: 10px;
  color: #fff;
  border-radius: 5px;
  outline: none;
  border: none;
  cursor: pointer;

  &.disabled {
    cursor: unset;
    background: gray;
  }
}
</style>
