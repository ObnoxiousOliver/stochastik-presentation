<template>
  <div class="root">
    <div class="center">
      <h2>zum Abschnitt springen</h2>
      <button @click="$emit('slide:to', 3)">01</button>
      <button @click="$emit('slide:to', 17)">02</button>
      <button @click="$emit('slide:to', 24)">03</button>
      <button @click="$emit('slide:to', 10)">04</button>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.root {
  background: white;
}

.slide {
  &-enter-active {
    transition: .7s;

    .center {
      z-index: 1;
      transition: .7s;
    }
  }
  &-enter-from {
    .center {
      opacity: 0;
      transform: translate(-50%, -50%) translateY(200%);
    }
  }
  &-leave-active {
    transition: .4s;

    .center {
      z-index: 1;
      transition: .4s;
    }
  }
  &-leave-to {
    .center {
      opacity: 0;
      transform: translate(-50%, -50%) translateX(-100%);
    }
  }
}

.center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

button {
  border: none;
  background: none;
  font-family: 'Staatliches', sans-serif;
  font-size: 7rem;
  cursor: pointer;
  margin: 0 40px 0 0;
  text-decoration: underline solid 8px;

  transition: .3s;

  &:hover {
    transform: scale(1.2);
  }
}
h2 {
  font-size: 2.5rem;
  font-family: 'Staatliches', sans-serif;
}
</style>
