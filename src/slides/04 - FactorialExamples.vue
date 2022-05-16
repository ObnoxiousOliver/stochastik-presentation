<template>
  <div class="root">
    <div class="ex1">
      <img class="tree" src="Tree.svg">
      <div class="poss poss3">3</div>
      <div class="poss poss2">2</div>
      <div class="poss poss1">1</div>

      <div class="equa math">
        3! = 3 × 2 × 1 = 6
      </div>
    </div>
    <div class="ex2">
      <h1>
        Kartenmischen<br>
        <i class="bi bi-suit-club-fill" />
        <i class="bi bi-suit-diamond" />
        <i class="bi bi-suit-spade-fill" />
        <i class="bi bi-suit-heart" />
      </h1>
      <p>
        Wie viele verschiedene Möglichkeiten gibt es ein Kartendeck mit <b>52 Karten</b> zu mischen?
      </p>

      <div class="res math">52!
        <span> = 8,065817517094388 × 10<sup>67</sup></span>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.root {
  background: white;
}

.ex1 {
  .equa {
    font-size: 3rem;
    position: absolute;
    top: 50%;
    right: 250px;
    transform: translateY(-50%) translateY(50px);
    opacity: 0;

    transition: .5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  }

  .tree {
    position: absolute;
    top: 200px;
    left: 50px;
    width: 500px;
    transform: rotate(-90deg);
  }

  .poss {
    font-size: 2rem;
    font-weight: 40px;
    position: absolute;
  }

  .poss3 {
    bottom: 20px;
    left: 160px + 50px;
  }
  .poss2 {
    bottom: 20px;
    left: 260px + 50px;
  }
  .poss1 {
    bottom: 20px;
    left: 360px + 50px;
  }
}

.ex2 {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%) translateY(80px);
  text-align: center;
  opacity: 0;
  width: fit-content;
  transition: .4s cubic-bezier(0.175, 0.885, 0.32, 1.275);

  h1 {
    font-family: 'Staatliches', sans-serif;
    font-size: 5rem;
    letter-spacing: 0.1em;
  }

  p {
    margin: 30px auto;
    font-size: 1.7rem;
    line-height: 1.5;
    width: 60%;
  }

  .res {
    margin: 50px 0 0;
    font-size: 4rem;
    justify-content: center;
    white-space: nowrap;
    transition: .4s cubic-bezier(0.175, 0.885, 0.32, 1.275);

    span {
      transition: .6s cubic-bezier(0.175, 0.885, 0.32, 1.275);
      transform: translate(0);
      width: 13.4em;
    }
  }
}

[state='1'] {
  .ex1 .equa {
    opacity: 1;
    transform: translateY(-50%);
  }
}

[state='2'], [state='3'], [state='4'] {
  .ex1 {
    opacity: 0;
  }
  .ex2 {
    opacity: 1;
  }
}

[state='2'], [state='1'] {
  .res {
    opacity: 0;
    transform: translateY(-120px);

    span {
      opacity: 0;
      width: 0;
      transform: translateX(-10%);
    }
  }
}
[state='3'] {
  .res {
    span {
      opacity: 0;
      width: 0;
      transform: translateX(-10%);
    }
  }
}

[state='3'], [state='4'] {
  .ex2 {
    transform: translate(-50%, -50%);
  }
}
</style>
