<template>
  <div class="calc">
    <div class="display">55544455</div>
    <div class="button">AC</div>
    <div class="button">+/-</div>
    <div class="button">%</div>
    <div class="button operator">÷</div>
    <div class="button">7</div>
    <div class="button">8</div>
    <div class="button">9</div>
    <div class="button operator">×</div>
    <div class="button">4</div>
    <div class="button">5</div>
    <div class="button">6</div>
    <div class="button operator">-</div>
    <div class="button">1</div>
    <div class="button">2</div>
    <div class="button">3</div>
    <div class="button operator">+</div>
    <div class="button">0</div>
    <div class="button">.</div>
    <div class="button">=</div>
    <div class="button operator">√</div>
  </div>
</template>

<script>
export default {
 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.calc{
  margin: 0 auto;
  width: 400px;
  font-size: 40px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}
.display{
  grid-column: 1/5;
  background-color: rgb(89, 89, 117);
  color: #fff;
}

.button{
  background-color: rgb(211, 194, 194);
  border: 1px solid #999;
}

.operator {
  background-color: rgb(164, 165, 235);
  color: #fff;
}

</style>
