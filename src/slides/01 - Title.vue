<template>
  <div class="root">
    <div>
      <h3>Alex | Julia | Sema | Oliver</h3>
      <h1>Fakultät!</h1>
      <h2>Stochastik</h2>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.root {
  background: white;

  display: grid;
  place-items: center;

  & > div {
    // text-align: center;
    transform: translateY(-10px);
  }
}

h1 {
  font-size: 120px;
  letter-spacing: 0.1em;
  font-family: 'Staatliches', sans-serif;
}

h2 {
  font-size: 30px;
  letter-spacing: 0.6em;
  text-transform: uppercase;
  margin: -30px 0 0;
}

h3 {
  font-weight: 300;
  margin: 0 0 -20px;
}

.slide {
  &-enter-active {
    transition: 1.5s cubic-bezier(0.19, 1, 0.22, 1);
    transition-delay: .5s;

    h2 {
      transition: 1.5s .8s cubic-bezier(0.19, 1, 0.22, 1);
      clip-path: inset(0);
    }
    h3 {
      transition: 1.5s 1s cubic-bezier(0.19, 1, 0.22, 1);
      clip-path: inset(0);
    }
  }

  &-enter-from {
    opacity: 0;
    transform: scale(1.2);

    h2 {
      transform: translateY(-100%);
      clip-path: inset(100% 0 0 0);
    }
    h3 {
      transform: translateY(100%);
      clip-path: inset(0 0 100% 0);
    }
  }

  &-leave-active {
    z-index: 1;
    transition: .5s cubic-bezier(0.55, 0.085, 0.68, 0.53);
  }
  &-leave-to {
    transform: translateY(-100%);
  }
}

</style>
