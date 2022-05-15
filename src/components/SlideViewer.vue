<template>
  <div
    class="slide-viewer"
    :style="{
      position: 'fixed',
      width: size.width + 'px',
      height: size.height + 'px',
      transformOrigin: '0 0',
      transform: `translate(${slidePos.x}px, ${slidePos.y}px) scale(${slidePos.scale})`
    }"
  >
    <!-- <canvas class="scene" id="three" :style="{
      transform: `scale(${1 / slidePos.scale})`,
      transformOrigin: '0 0'
    }" /> -->
    <transition name="slide">
      <component
        v-if="slideEl"
        :is="slideEl?.c"
        @slide:next="$emit('slide:next')"
        :state="slideEl.r.indexOf(slide)"
      />
    </transition>
    <div class="overlay">
      <div class="slide-controls">
        <span class="slide-number">
          {{ slide }} / {{ maxSlide }}
        </span>
        <button @click="toggleFullscreen" class="slide-control-btn">
          <i class="bi-fullscreen"/>
        </button>
        <button @click="$emit('slide:prev')" class="slide-control-btn">
          <i class="bi-chevron-left"/>
        </button>
        <button @click="$emit('slide:next')" class="slide-control-btn">
          <i class="bi-chevron-right"/>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { computed, onMounted, ref } from '@vue/runtime-core'

import StartSlide from '../slides/00 - StartSlide.vue'
import TitleSlide from '../slides/01 - Title.vue'
import FactorialSlide from '../slides/02 - Factorial.vue'

export default {
  props: {
    slide: Number,
    maxSlide: Number
  },

  setup (props) {
    const slides = [
      { r: [0], c: StartSlide },
      { r: [1], c: TitleSlide },
      { r: [2], c: FactorialSlide }
    ]

    const slideEl = computed(() => slides.find(x => x.r.includes(props.slide)))

    const size = {
      width: 1280,
      height: 720
    }

    const slidePos = ref({
      x: 0,
      y: 0,
      scale: 1
    })

    function updatePos () {
      const width = window.innerWidth
      const height = window.innerHeight

      const wide = width / size.width > height / size.height

      slidePos.value.x = wide ? (width - size.width * (height / size.height)) / 2 : 0
      slidePos.value.y = wide ? 0 : (height - size.height * (width / size.width)) / 2

      slidePos.value.scale = Math.min(width / size.width, height / size.height)
    }

    onMounted(() => {
      updatePos()
      window.addEventListener('resize', updatePos)
      // init()
    })

    function toggleFullscreen () {
      if (document.fullscreenElement) {
        document.exitFullscreen()
      } else {
        document.documentElement.requestFullscreen()
      }
    }

    return {
      slideEl,
      size,
      slidePos,
      toggleFullscreen
    }
  }
}
</script>

<style lang="scss" scoped>
.slide-viewer {
  overflow: hidden;

  & > * {
    position: absolute;
    inset: 0;
  }

  .overlay {
    pointer-events: none;

    .slide-number {
      color: white;
      font-size: 12px;
      line-height: 28px;
      margin: 0 10px;
    }

    .slide-controls {
      position: absolute;
      inset: auto 0 0 auto;
      margin: 5px;
      display: flex;
      gap: 5px;
      opacity: 0.5;
    }

    .slide-control-btn {
      appearance: none;
      border: none;

      background: #0008;
      color: #fff;
      border-radius: 50%;
      font-size: 12px;
      width: 28px;
      height: 28px;

      cursor: pointer;
      pointer-events: all;
    }
  }
}
</style>
