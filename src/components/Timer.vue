<template>
  <div class="all">
     <div>Time</div>
     <!-- <p id="time">{{ timer }}</p> -->
     <p> {{ hr }} :{{ min }} : {{ sec }} : {{ mils }}</p>

      <Control title="Start" :control="start"/>
     <Control title="Stop" :control="stop"/>

     
</div>
<p>Watch</p>
</template>


<script>

import Control from './Control.vue';
export default{
    name: `Timer`,
    components:{
        Control,



    },
    data(){
        return{
            timerId:0,
            timer:0,
            mils:0,
            sec:0,
            min:0,
            hr:0
        }
    },
    methods:{
        msg(){
            alert("button call")
        },
        start(){
            this.timerId=setInterval(()=>{
                this.mils++
                if(this.mils==100){
                    this.sec++;
                   this.mils=0;
                }
                if(this.sec==60){
                    this.min++;
                    this.sec=0;
                }
                if(this.min==60){
                    this.hr++;
                    this.sec=0;
                }




            },100);
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
    padding-top: 50px;
    border: 10px solid rgb(219, 48, 114);
    border-radius: 20%;


}




</style>




