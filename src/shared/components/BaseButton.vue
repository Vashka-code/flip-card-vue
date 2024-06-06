<template>
  <button
    class="button"
    :class="{ disabled: props.disabled }"
    :disabled="props.disabled"
    :onclick="props.handleClick"
  >
    {{ props.buttonText }}
  </button>
</template>

<script setup lang="ts">
const props = defineProps<{
  buttonText: string
  disabled?: boolean
  handleClick?: void
}>()
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
