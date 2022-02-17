<template>
  <div class="spinner">
    <div class="gameboard" :style="buildPie">
     <div class="spinnerCharacter" :style="{backgroundImage:`url(${roman})` }">
       <img class="arm" :class="{spinning: isSpinning}" :src="require('@/assets/arm2.png')" alt="">
     </div>
    </div>
     <div class="list">
       <ul>
        <li  v-for="choice in choices" :key="choice">
          {{choice.name}} <span class="colorbox" :style="{backgroundColor: choice.color}"></span>
        </li>
       </ul>
       <button @click="spin">Spin Roman</button>
      </div>
  </div>
</template>

<script>
var roman = require('@/assets/roman.png');
export default {
  name: 'Spinner',
  props: ['users'],
  data(){
    return {
      choices:this.users,
      roman: roman,
      isSpinning: false,
      rand: `rotate(1200deg)`,
    }
  },
  computed: {
    buildPie(){
      var css = '';
      var percent = 100 / this.users.length;
      var count = percent;
      for (var i = 0; i<this.users.length; i++){
        var person = this.users[i]
        var newcss = i < this.users.length-1 ? `${person.color} 0, ${person.color} ${count}%, ` :  `${person.color} 0, ${person.color} ${count}%`
        css += newcss
        count += percent
      }
      return  `
      background:
		  radial-gradient(
        circle closest-side,
        transparent 100%,
        white 0
		  ),
      conic-gradient(
        ${css}
    );`
    
    },
  },
  methods: {
    spin: function(){
      this.isSpinning = !this.isSpinning
    },
    randNumber(){
      var numb = Math.random() * (2160 - 720) + 720;
      debugger; //eslint-disable-line
      return `rotate(${numb}deg)`;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.spinnerCharacter {
  position:absolute;
  width:400px;
  height:400px;
  background-repeat:no-repeat;
  display:flex;
  justify-content:center;
  align-items:center;
  transform:translate(42px, 0)
}

.arm {
  position:absolute;
  left:-238px;
  bottom:130px;
  transform-origin: right 38px;

}

.spinning {
  animation: spin 3s ease-out 0s 1 normal forwards;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  50%,
  100% {
    transform: v-bind('randNumber()');
  }
}

.spinner {
  position:relative;
  display:flex;
  justify-content:center;
  align-items:center;
  height:100%;
}

.gameboard  {
  width:95vh;
  height:95vh;
  border-radius:50%;
  display:flex;
  justify-content:center;
  align-items:center;
}

.list {
  margin-left:5vh;
  flex-direction:column;
  display:flex;
}

.list ul {
    margin:0;
  padding:0;

}

.list li {
  list-style-type:none;
  text-align:right;
  display:flex;
  margin-bottom:5px;
  justify-content:flex-end;
  align-items:center;
}

.colorbox {
  width:30px;
  height:30px;
  display:inline-block;
  margin-left:10px;
}
</style>
