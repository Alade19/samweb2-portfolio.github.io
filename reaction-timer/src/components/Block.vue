<template>
    <div class="box" v-if="showblock" @click="endgame">
        <p>Click me</p>
    </div>
</template>
<script>
export default {
    props:['timer'],
    data(){
        return{
            showblock: false,
            timecount: 0,
            intervalid: null,
        }
    },
    mounted() {
        setTimeout(() => {
           this.showblock =true
        }, this.timer);
    },
    updated() {
        this.intervalid = setInterval(() => {
            this.timecount += 10
        }, 10);
    },
    methods:{
        endgame(){
            clearInterval(this.intervalid)
            this.$emit('end',this.timecount)
        }
    }
}
</script>
<style>
   .box{
    color: white;
    background: rgba(25, 90, 25, 0.897);
    border-radius: 20px;
    width: 400px;
    padding: 100px 0;
    text-align: center;
    margin: 0 auto;
    cursor: pointer;
    margin-top: 25px;
    font-size: 20px;
   } 
</style>