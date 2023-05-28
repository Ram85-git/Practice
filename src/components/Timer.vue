<template>
  <div class="all">
     <div>Time</div>
     <p id="time">{{ timer }}</p>

      <Control title="Start" :control="start"/>
     <Control title="Stop" :control="stop"/>
</div>
</template>


<script>

import Control from './Control.vue';
export default{
    name: `Timer`,
    components:{
        Control
    },
    data(){
        return{
            timer:0
        }
    },
    methods:{
        msg(){
            alert("button call")
        },
        start(){
            this.timerId=setInterval(()=>{
                this.timer++;
            },1000 );
        },
        stop(){
            clearInterval(this.timerId);
        }
    }





}




</script>
<style scoped>
.all{
    background-color: rgb(0, 217, 255);
    height: 200px;
    width: 200px;
    margin: auto;
    padding: 50px;
    border: 10px solid rgb(219, 48, 114);
    border-radius: 20%;


}




</style>




