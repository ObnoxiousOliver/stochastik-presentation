<template>
  <div class="root">
    <img src="Tree2.svg">

    <div class="prob4">4</div>
    <div class="probx">×</div>
    <div class="prob3">3</div>

    <div class="math given">n = 4 &nbsp;&nbsp;&nbsp;&nbsp; k = 2</div>
    <div class="math formula">
      <span class="frac">
        <span>n!</span>
        <span>(n - k)!</span>
      </span>
    </div>
    <div class="math equa">
      <span style="width: 3.1em" class="frac f1">
        <span>4!</span>
        <span>(4 - 2)!</span>
      </span>
      <span style="width: 1.2em" class="f2">&nbsp;=&nbsp;</span>
      <span style="width: 1em" class="frac f2">
        <span>4!</span>
        <span>2!</span>
      </span>
      <span style="width: 1.2em" class="f3">&nbsp;=&nbsp;</span>
      <span style="width: 5.7em" class="frac f3">
        <span>4 × 3 × <s>2 × 1</s></span>
        <span><s>2 × 1</s></span>
      </span>
      <span style="width: 5.5em" class="f4">&nbsp;= 4 × 3 = 12</span>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.root {
  background: white;

  font-size: 2rem;
}

img {
  position: absolute;
  top: 130px;
  left: 50%;
  transform: translateX(-50%);
}

s {
  text-decoration: line-through red 0.1em;
}

.given {
  font-size: 2.5rem;
  position: absolute;
  top: 30px;
  left: 50%;
  transform: translateX(-50%);
}

.equa {
  font-size: 3rem;
  position: absolute;
  top: 520px;
  left: 50%;
  transform: translateX(-50%);
  white-space: nowrap;

  & > span {
    transition: .6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    transform: translate(0);
  }
}

.prob3 {
  position: absolute;
  top: 380px;
  left: 200px;
}
.prob4 {
  position: absolute;
  top: 230px;
  left: 200px;
}
.probx {
  position: absolute;
  top: 310px;
  left: 200px;
}

.formula {
  font-size: 3rem;
  position: absolute;
  top: 260px;
  right: 70px;

  transition: .2s;
}

[state='0'], [state='1'] {
  .f1 {
    opacity: 0;
    width: 0 !important;
    transform: translateX(-70%);
  }
  .f2 {
    opacity: 0;
    width: 0 !important;
    transform: translateX(-70%);
  }
  .f3 {
    opacity: 0;
    width: 0 !important;
    transform: translateX(-70%);
  }
  .f4 {
    opacity: 0;
    width: 0 !important;
    transform: translateX(-70%);
  }
}
[state='2'] {
  .f2 {
    opacity: 0;
    width: 0 !important;
    transform: translateX(-70%);
  }
  .f3 {
    opacity: 0;
    width: 0 !important;
    transform: translateX(-70%);
  }
  .f4 {
    opacity: 0;
    width: 0 !important;
    transform: translateX(-70%);
  }
}
[state='3'] {
  .f3 {
    opacity: 0;
    width: 0 !important;
    transform: translateX(-70%);
  }
  .f4 {
    opacity: 0;
    width: 0 !important;
    transform: translateX(-70%);
  }
}
[state='4'] {
  .f4 {
    opacity: 0;
    width: 0 !important;
    transform: translateX(-70%);
  }
}

[state='0'] {
  .formula {
    opacity: 0;
  }
}
</style>
