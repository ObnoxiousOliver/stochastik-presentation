<template>
  <div style="position: fixed; opacity: 0;">
  </div>
  <SlideViewer
    v-if="allAssetsLoaded"
    :slide="slide"
    :maxSlide="maxSlide"
    @slide:next="slide++"
    @slide:prev="slide--"
  />
  <div class="loading" v-else>Loading...</div>
</template>

<script>
import { ref } from '@vue/reactivity'
import SlideViewer from './components/SlideViewer.vue'
import { onMounted, watch } from '@vue/runtime-core'

export default {
  name: 'App',
  components: {
    SlideViewer
  },

  setup () {
    const slide = ref(0)
    const maxSlide = 23
    const allAssetsLoaded = ref(false)

    watch(slide, () => {
      slide.value = Math.max(0, Math.min(slide.value, maxSlide))
      localStorage.setItem('slide', slide.value)
    })

    onMounted(() => {
      const totalImg = document.querySelectorAll('img').length

      slide.value = localStorage.getItem('slide') ?? 0

      let loadedImg = 0

      document.querySelectorAll('img').forEach(x => x.addEventListener('load', () => {
        loadedImg++

        if (loadedImg >= totalImg) {
          allAssetsLoaded.value = true
        }
      }))
      if (loadedImg >= totalImg) {
        allAssetsLoaded.value = true
      }
    })

    document.addEventListener('keydown', (e) => {
      if (e.key === 'ArrowRight') {
        slide.value++
      }
      if (e.key === 'ArrowLeft') {
        slide.value--
      }
    })

    return {
      slide,
      allAssetsLoaded,
      maxSlide
    }
  }
}
</script>

<style lang="scss">
@import url("https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.1/font/bootstrap-icons.css");
@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Raleway:wght@100;200;300;400;500;600;700;800;900&display=swap');

*, ::before, ::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  user-select: none;

  font-family: 'Poppins', sans-serif;
}

body {
  background: #000;
}

.loading {
  position: fixed;
  inset: 0;
  display: flex;
  justify-content: center;
  align-items: center;

  color: #fff;
}
</style>
