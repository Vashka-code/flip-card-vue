<template>
  <div class="game">
    <ul class="game__list">
      <li
        v-for="(_, index) in Array.from({ length: props.count })"
        :key="index"
        :class="{ deletedItem: index === 1 && isAnimationFinished }"
      >
        <flip-card :start-animation="index === 1 && isStartAnimation" />
      </li>
    </ul>

    <base-button
      :button-text="'Start Animation'"
      :disabled="isStartAnimation"
      :handle-click="startAnimation"
    />
  </div>
</template>

<script setup lang="ts">
import FlipCard from '../../shared/components/FlipCard.vue'
import BaseButton from '../../shared/components/BaseButton.vue'
import { ref } from 'vue'

const props = defineProps<{
  count: number
}>()

const isStartAnimation = ref(false)
const isAnimationFinished = ref(false)

const startAnimation = () => {
  isStartAnimation.value = true

  setTimeout(() => {
    isAnimationFinished.value = true
  }, 2000)
}
</script>

<style lang="scss" scoped>
.game {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  align-items: center;
  gap: 20px;
  min-height: 665px;

  @media screen and (max-width: 768px) {
    min-height: 385px;
  }

  &__list {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-wrap: wrap;
    gap: 20px;

    @media screen and (max-width: 768px) {
      gap: 10px;
    }
  }
}
.deletedItem {
  position: absolute;
}
</style>
