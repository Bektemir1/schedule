<template>
 <div class="container app">
   <div class="row">
     <div class="col-lg-5">
       <Gradation
        :gradation="timing"
       />
     </div>
     <div class="col-lg-7 box">
       <table id="myTable"></table>
       <Schedule 
       :schedule="timing"
       @selectDate="selectDate"
      
       />
     </div>
   </div>

   
 </div>
</template>

<script>
// import $ from 'jquery'
import Schedule from './components/Schedule.vue';
import Gradation from './components/Gradation.vue';

export default {
  name: 'App',
  components:{
    Schedule,
    Gradation
  },
  
  data(){
    return {
      timing:[],
      gradation:{
        duration:0
      }
   
     }
  },

  methods:{

    generateTime(){
      let today = new Date()
      let hour = 8;
      let min = 15;
      today.setHours(8,0);
      this.timing.push({
        date:new Date(today),
        type:'Свободно',
        isShow:false,
        duration:0
       
      })
      console.log(today)
      for(let i=0;i<10;i++){
        for(let j=0; j<=3; j++){
          today.setHours(hour,min)
          this.timing.push({
            date:new Date(today),
            type:'Свободно',
            isShow:false,
            duration:0
          })
          min+=15;
          }
        }
      },

      selectDate(obj){
        console.log(obj)
        this.timing.map((item)=>{
          if(item.date.getHours() === obj.hour && item.date.getMinutes()=== obj.min){
            item.isShow = !item.isShow;
            if(item.date.getHours() === 9 && item.date.getMinutes() === 0 || item.date.getHours() === 9 && item.date.getMinutes()=== 15){
              item.type = 'Занят';
              item.isShow ? item.duration+=15 : item.duration -=15
            }
            if(item.date.getHours() === 8 && item.date.getMinutes() === 15){
              item.type = 'Занят';
              item.isShow ? item.duration+=15 : item.duration -=15
             
              
            }
            if(item.date.getHours() === 16){
              item.type = 'Занят'
              item.isShow ? item.duration+=15 : item.duration -=15
            }
           }
        })
      }
   
  },
  mounted(){
    this.generateTime()
  
     
    }
 }
</script>

<style>

.app{
  margin:100px;
}
.box{
    overflow:auto;
    height:70vh;
}

</style>
