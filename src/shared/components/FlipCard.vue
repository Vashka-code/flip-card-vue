<template>
  <div class="flipcard" :class="{ animation: props.startAnimation, open: props.open }">
    <div class="flipcard__front">
      <img class="flipcard__img" src="../assets/card-front.svg" alt="" />
    </div>
    <div class="flipcard__back">
      <img class="flipcard__img" src="../assets/card.svg" alt="" />
    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps<{
  startAnimation?: boolean
  open?: boolean
}>()
</script>

<style lang="scss" scoped>
$heightProportion: 1.49;

.flipcard {
  $self: &;

  width: 185px;
  height: calc(185px * $heightProportion);
  position: relative;
  perspective: 1000px;

  @media screen and (max-width: 768px) {
    width: 100px;
    height: calc(100px * $heightProportion);
  }

  &__front,
  &__back {
    position: absolute;
    width: 100%;
    height: 100%;
    left: 0;
    top: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    backface-visibility: hidden;
  }

  &__front {
    transform: rotateY(180deg);
  }

  &.animation {
    transition: 1s;
    transition-delay: 1s;
    transform: translateY(-120%);

    #{$self}__front,
    #{$self}__back {
      transition: 1s;
    }
    #{$self}__front {
      transform: rotateY(360deg);
    }
    #{$self}__back {
      transform: rotateY(180deg);
    }
  }

  &.open {
    #{$self}__front {
      transform: rotateY(360deg);
    }
    #{$self}__back {
      transform: rotateY(180deg);
    }
  }

  &__img {
    width: 100%;
    object-fit: contain;
  }
}
</style>
