<template>
  <div class="calc">
    <div class="display">{{ presentValue || "0" }}</div>
    <div @click="clear" class="button">AC</div>
    <div @click="sign" class="button">+/-</div>
    <div @click="percent" class="button">%</div>
    <div @click="divide" class="button operator">÷</div>
    <div @click="append('7')" class="button">7</div>
    <div @click="append('8')" class="button">8</div>
    <div @click="append('9')" class="button">9</div>
    <div @click="multiply" class="button operator">×</div>
    <div @click="append('4')" class="button">4</div>
    <div @click="append('5')" class="button">5</div>
    <div @click="append('6')" class="button">6</div>
    <div @click="subtract" class="button operator">-</div>
    <div @click="append('1')" class="button">1</div>
    <div @click="append('2')" class="button">2</div>
    <div @click="append('3')" class="button">3</div>
    <div @click="addition" class="button operator">+</div>
    <div @click="append('0')" class="button">0</div>
    <div @click="dot" class="button">.</div>
    <div @click="equalTo" class="button">=</div>
    <div class="button operator">√</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      previousValue: null,
      presentValue: "",
      operatorValue: null,
      clickedOperator: false
    };
  },
  methods: {
    clear() {
      this.presentValue = "";
    },
    sign() {
      if (this.presentValue.charAt(0) === "-") {
        return (this.presentValue = this.presentValue.slice(1));
      } else {
        return (this.presentValue = `-${this.presentValue}`);
      }
    },
    percent() {
      this.presentValue = `${parseFloat(this.presentValue) / 100}`;
    },
    append(number) {
      if (this.clickedOperator) {
        this.presentValue = "";
        this.clickedOperator = false;
      }
      this.presentValue = `${this.presentValue}${number}`;
    },
    dot() {
      if (this.presentValue.indexOf(".") === -1) {
        this.append(".");
      }
    },
    myOperatorHelper() {
      this.previousValue = this.presentValue;
      this.clickedOperator = true;
    },
    divide() {
      this.operatorValue = (num1, num2) => num1 / num2;
      this.myOperatorHelper();
    },
    subtract() {
      this.operatorValue = (num1, num2) => num1 - num2;
      this.myOperatorHelper();
    },
    addition() {
      this.operatorValue = (num1, num2) => num1 + num2;
      this.myOperatorHelper();
    },
    multiply() {
      this.operatorValue = (num1, num2) => num1 * num2;
      this.myOperatorHelper();
    },
    equalTo() {
      this.presentValue = `${this.operatorValue(
        parseFloat(this.presentValue),
        parseFloat(this.previousValue)
      )}`;
      this.previousValue = null;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.calc {
  margin: 0 auto;
  width: 400px;
  font-size: 40px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}
.display {
  grid-column: 1/5;
  background-color: rgb(89, 89, 117);
  color: #fff;
}

.button {
  background-color: rgb(211, 194, 194);
  border: 1px solid #999;
}

.operator {
  background-color: rgb(164, 165, 235);
  color: #fff;
}
</style>
