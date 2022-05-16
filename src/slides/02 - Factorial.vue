<template>
  <div class="root">
    <div class="fact1 abs math">
      <span>n!</span> <span class="f1">= n </span>
      <span class="f2">× (n - 1) × </span>
      <span class="f3">(n - 2) × </span>
      <span class="f4">... × 1</span>
    </div>
    <div class="fact2 abs math">
      <span>5! </span> <span
        class="f2">= 5 × 4 × 3 × 2 × 1</span><span
        class="f1">= 5 × (5 - 1) × (5 - 2) × (5 - 3) × (5 - 4)</span>
        <span class="f3">= 120</span>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.root {
  background: white;
  font-size: 60px;
}

.slide {
  &-enter-active {
    transition: .6s;

    .fact1 {
      z-index: 1;
      transition: .6s;
    }
  }
  &-enter-from {
    .fact1 {
      opacity: 0;
      transform: translate(-50%, -50%) translateY(200%);
    }
  }
}

.abs {
  position: absolute;
}

.math {
  font-family: Georgia, 'Times New Roman', Times, serif;
}

.fact1, .fact2 {
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: fit-content;

  transition: .4s cubic-bezier(0.175, 0.885, 0.32, 1.275);

  span {
    display: inline-block;
    white-space: nowrap;
    transition: .6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    transform: translate(0);
  }
}

.fact1 {
  .f1 { width: 1.7em; }
  .f2 { width: 4.65em; }
  .f3 { width: 3.8em; }
  .f4 { width: 3em; }
}

.fact2 {
  opacity: 0;
  transform: translate(-50%, -50%) translateY(100px);

  .f1 { width: 16.6em; }
  .f2 {
    width: 0;
    opacity: 0;
  }
  .f3 {
    width: 0;
    opacity: 0;
    transform: translateX(-70%);
  }
}

[state='0'] {
  .f1, .f2, .f3, .f4 {
    width: 0;
    opacity: 0;
    transform: translateX(-70%);
  }
}
[state='1'] {
  .f2, .f3, .f4 {
    width: 0;
    opacity: 0;
    transform: translateX(-70%);
  }
}
[state='2'] {
  .f3, .f4 {
    width: 0;
    opacity: 0;
    transform: translateX(-70%);
  }
}
[state='3'] {
  .f4 {
    width: 0;
    opacity: 0;
    transform: translateX(-70%);
  }
}

[state='5'],
[state='6'],
[state='7'],
[state='8'] {
  .fact1 {
    transform: translate(-50%, -50%) translateY(-230px) scale(0.8);
  }
  .fact2 {
    opacity: 1;
    transform: translate(-50%, -50%);
  }
}

[state='4'],
[state='5'] {
  .fact2 {
    .f1 {
      width: 0;
      opacity: 0;
      transform: translateX(-30%);
    }
  }
}
[state='7'],
[state='8'] {
  .fact2 {
    span {
      transition: .4s;
    }

    .f1 {
      width: 0;
      opacity: 0;
      transform: translateX(-16.6em * 0.5);
    }
    .f2 {
      width: 8.3em;
      opacity: 1;
    }
  }
}
[state='8'] {
  .fact2 {
    .f3 {
      width: 3em;
      opacity: 1;
      transform: translateX(0);
    }
    span {
      transition: .6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    }
  }
}
</style>
