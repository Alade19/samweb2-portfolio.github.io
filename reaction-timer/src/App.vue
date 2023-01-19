<template>
 <h2 class="title">{{title}}</h2>
 <button @click="startgame" :disabled="isstart" class="btn">play</button>
 <Block v-if="isstart" @end="endgame" :timer="timer"/>
 <Result v-if="showresult" :score="score"/>
</template>

<script>
import Block from "./components/Block.vue"
import Result from "./components/Result.vue"

export default {
  name: 'App',
  components: { Block,Result},
  data(){
    return{
      title: "Ninja Reaction Timer",
      isstart: false,
      timer: null,
      score: null,
      showresult: false
    }
  },
  methods:{
    startgame(){
      this.isstart = true
      this.timer = 2000 + Math.random() * 5000
      this.showresult = false
    },
    endgame(timecount){
      this.isstart = false
      this.score = timecount
      this.showresult = true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
.title{
  color: black;
}
.btn{
  color: white;
  background: green;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
}
.btn[disabled]{
  opacity: 0.5;
  cursor: not-allowed;
}
</style>
