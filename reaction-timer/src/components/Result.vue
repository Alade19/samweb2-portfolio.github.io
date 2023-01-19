<template lang="">
    <div>
        <p class="res">Reaction time - {{this.score}} ms</p>
        <p class="rating">{{rating}}</p>
    </div>
</template>
<script>
export default {
    props:['score'],
    data(){
        return{
            rating: null,
        }
    },
    mounted(){
        if(this.score < 240){
            this.rating = 'Ninja Fingers'
        }else if (this.score < 580){
            this.rating = 'Rapid Reflexes'
        }else{
            this.rating = 'Snail Pace ....'
        }
    }
}
</script>
<style>
   .res{
    font-size: 17px;
    font-style: italic;
   }
   .rating{
    font-style: italic;
    color: green;
    font-size: 21px;
   } 
</style>