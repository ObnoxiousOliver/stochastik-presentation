<template>
  <div class="root">
    <span>
      {{ (((state ?? 0) + 1) + '').padStart(2, '0') }}
    </span>
  </div>
</template>

<script lang="ts" setup>
import { defineProps } from 'vue'

defineProps({
  state: Number
})
</script>

<style lang="scss" scoped>
span {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-family: 'Staatliches', cursive;
  font-size: 7rem;
}

.slide {
  &-enter-active {
    transition: .4s;
  }
  &-enter-from {
    transform: translateY(10%);
  }
  &-leave-active {
    z-index: 1;
    transition: .4s;
  }
  &-leave-to {
    opacity: 0;
    transform: translateY(-10%);
  }
}
</style>
