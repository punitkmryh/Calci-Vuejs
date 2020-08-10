<template>
  <div class="calulator">
    <div class="display">{{ current || 0 }}</div>
    <div @click="clear" class="geybtn">AC</div>
    <div @click="sign" class="geybtn">+/-</div>
    <div @click="percent" class="geybtn">%</div>
    <div @click="divide" class="btn-operator">÷</div>
    <div @click="append('7')" class="btn">7</div>
    <div @click="append('8')" class="btn">8</div>
    <div @click="append('9')" class="btn">9</div>
    <div @click="multiply" class="btn-operator">x</div>
    <div @click="append('4')" class="btn">4</div>
    <div @click="append('5')" class="btn">5</div>
    <div @click="append('6')" class="btn">6</div>
    <div @click="minus" class="btn-operator">-</div>
    <div @click="append('1')" class="btn">1</div>
    <div @click="append('2')" class="btn">2</div>
    <div @click="append('3')" class="btn">3</div>
    <div @click="add" class="btn-operator">+</div>
    <div @click="append('0')" class="btn zero">0</div>
    <div @click="dot" class="btn">.</div>
    <div @click="equal" class="btn-operator">=</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      previous:null,
      current: "", //binded to display
      operator:null,
      operatorClick:false
    };
  },
  methods: {
    clear() {
      this.current = "";
    },
    sign() {
      this.current =
        this.current.charAt(0) === "-"
          ? this.current.slice(1)
          : `-${this.current}`;
    },
    percent() {
      this.current = `${parseFloat(this.current) / 100}`;
    },
    append(num) {
      if(this.operatorClick){
        this.current='';
        this.operatorClick=false;
      }
      this.current = `${this.current}${num}`;
    },
    dot() {
      if (this.current.indexOf(".") === -1) {
        this.append(".");
      }
    },
    setPrevious(){
      this.previous=this.current;
      this.operatorClick=true;
    },
    divide(){
      // operator(a,b)
      this.operator = (a,b)=>a/b;
      this.setPrevious();
    },
    multiply(){
      this.operator = (a,b)=>a*b;
      this.setPrevious();
    },
    minus(){
      this.operator = (a,b)=>a-b;
      this.setPrevious();
    },
    add(){
      this.operator = (a,b)=>a+b;
      this.setPrevious();
    },
    equal(){
      this.current = `${this.operator(
        parseFloat(this.current),
        parseFloat(this.previous)
        )}`;
      this.previous=null;

    }

  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  box-sizing: border-box;
  font-family: "Roboto", sans-serif;
}
.calulator {
  display: grid;
  width: 400px;
  margin: 0 auto;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  /* grid-auto-columns: (20px, auto); */
  margin-top: 30px;
  font-size: 20px;
  box-shadow: 0 8px 50px -7px black;
}

.display {
  grid-column: 1/5;
  font-size: 2.4rem;
  font-weight: lighter;
  background-color: #333;
  color: white;

  /* text-align:end; */
  height: 90px;
  border: none;
  text-align: right;
  padding: 1.5rem;
}

.zero {
  grid-column: 1/3;
}
.btn {
  background-color: #616163;
  border: 1px solid #303030;
  color: #f2f2f2;
  padding: 0.8rem;
  font-weight: 200;
  cursor: pointer;
}
.blink-me {
  color: #e0b612;
}

.geybtn {
  background-color: #424345;
  font-weight: 200;
  border: 1px solid #303030;
  color: #f2f2f2;
  padding: 0.8rem;
  cursor: pointer;
}
.btn:hover {
  background: #f49e3f;
}
.geybtn:hover {
  background: #f49e3f;
}
.operator {
  background-color: #f49e3f;
  color: aliceblue;
}

.btn-operator {
  background-color: #f49e3f;
  font-weight: 200;
  border: 0.01cm solid #616163;
  color: #f2f2f2;
  padding: 0.8rem;
  cursor: pointer;
}

.btn-operator:hover {
  background: #333;
}
</style>
