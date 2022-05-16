<template>
  <div class="root">
    <div class="math given">n = 6 &nbsp;&nbsp;&nbsp;&nbsp; k = 3</div>
    <div class="math equa">6 × 5 × 3 = 90</div>
    <div class="math formula">
      <span class="frac">
        <span>n!</span>
        <span>k!</span>
      </span>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.root {
  background: white;
  padding: 50px;
  font-size: 2rem;
}

.math {
  font-family: Georgia, 'Times New Roman', Times, serif;
}

.frac {
  display: inline-flex;
  flex-flow: column nowrap;
  span:not(:last-child) {
    border-bottom: #000 solid .1em;
  }
}
</style>
