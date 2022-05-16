<template>
  <div class="root">
    <div class="math given">n = 4 &nbsp;&nbsp;&nbsp;&nbsp; k = 3</div>

    <table>
      <tr>
        <td>A B C</td>
        <td>A B D</td>
        <td>A C D</td>
        <td>B C D</td>
      </tr>
      <tr>
        <td>A C B</td>
        <td>A D B</td>
        <td>A D C</td>
        <td>B D C</td>
      </tr>
      <tr>
        <td>B A C</td>
        <td>B A D</td>
        <td>C A D</td>
        <td>C B D</td>
      </tr>
      <tr>
        <td>B C A</td>
        <td>B D A</td>
        <td>C D A</td>
        <td>C D B</td>
      </tr>
      <tr>
        <td>C A B</td>
        <td>D A B</td>
        <td>D A C</td>
        <td>D B C</td>
      </tr>
      <tr>
        <td>C B A</td>
        <td>D B A</td>
        <td>D C A</td>
        <td>D C B</td>
      </tr>
    </table>

    <div class="row1">
      <div class="math amount">
        <span class="frac">
          <span>4!</span>
          <span>(4 - 3)!</span>
        </span>
        &nbsp;=&nbsp;
        <span class="frac">
          <span>4!</span>
          <span>1!</span>
        </span>
        &nbsp;= 24
      </div>
      <div class="math res">
        24 ÷ 6 = 4
      </div>
    </div>
    <div class="math formula">
      <span class="frac">
        <span>n!</span>
        <span>(n - k)! × k!</span>
      </span>
    </div>
  </div>
</template>

<style lang="scss" scoped>
table {
  position: absolute;
  top: 400px;
  left: 50%;
  transform: translate(-50%, -50%);

  font-family: 'Staatliches', sans-serif;
  font-size: 3rem;
  border-spacing: 2px;

  td {
    padding: 0 40px;
    white-space: nowrap;
    line-height: 1.1;

    &:nth-child(1) {
      background: #ffc0cb;
    }
    &:nth-child(2) {
      background: #ffd7c0;
    }
    &:nth-child(3) {
      background: #f6ffc0;
    }
    &:nth-child(4) {
      background: #c0fffc;
    }
    &:nth-child(5) {
      background: #c0d6ff;
    }
    &:nth-child(6) {
      background: #edc0ff;
    }
  }
}

.given {
  position: absolute;
  top: 40px;
  left: 50%;
  transform: translateX(-50%);
  font-size: 3rem;
}

.row1 {
  position: absolute;
  top: 160px;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 2rem;
  display: flex;
}

.amount {
  margin-right: 40px;
}

.formula {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 2rem;
}
</style>
