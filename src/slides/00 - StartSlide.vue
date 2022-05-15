<template>
  <div>
    <button @click="click">
      <i class="bi-play"/>
    </button>
    Starte Präsentation
  </div>
</template>

<script>
export default {
  setup (props, { emit }) {
    async function click () {
      await document.documentElement.requestFullscreen()

      emit('slide:next')
    }

    return {
      click
    }
  }
}
</script>

<style lang="scss" scoped>
div {
  display: flex;
  flex-flow: column;
  justify-content: center;
  align-items: center;
  gap: 20px;
  color: #555;
}

.slide {
  &-leave-active {
    transition: opacity 0.2s;
  }
  &-leave-to {
    opacity: 0;
  }
}

button {
  appearance: none;

  border: #555 solid 2px;
  border-radius: 50%;
  background: none;
  color: #fff;
  font-size: 50px;
  padding: 4px 0 0 4px;

  width: 100px;
  height: 100px;

  cursor: pointer;
}
</style>
