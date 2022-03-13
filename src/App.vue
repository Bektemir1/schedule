<template>
 <div class="container app">
   <div class="row">
     <div class="col-lg-5">
       <Gradation
        :gradation="schedule"
       />
     </div>
     <div class="col-lg-7 box">
       <Schedule 
       :schedule="schedule"
       v-on:showSchedule="showSchedule"
       />
     </div>
   </div>

   
 </div>
</template>

<script>
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
    
      gradation:[
        {

        }
      ],
      schedule: [
        {time:'08:00 - 08:15', type: 'Свободно', isShow:false},
        {time:'08:15 - 08:30', type: 'Занят', isShow:false, duration:15},
        {time:'08:30 - 08:45', type: 'Свободно', isShow:false},
        {time:'08:45 - 09:00', type: 'Свободно', isShow:false},
        {id:5, time:'09:00 - 09:15', type: 'Занят', isShow:false, duration:15},
        {id:6, time:'09:15 - 09:30', type: 'Занят', isShow:false , duration:15},
        {id:7, time:'09:30 - 09:45', type: 'Занят', isShow:false, duration:15},
        {time:'09:45 - 10:00', type: 'Свободно', isShow:false},
        {time:'10:00 - 10:15', type: 'Свободно', isShow:false},
        {time:'10:15 - 10:30', type: 'Свободно', isShow:false},
        {time:'10:30 - 10:45', type: 'Свободно', isShow:false},
        {time:'10:45 - 11:00', type: 'Свободно', isShow:false},
        {time:'11:00 - 11:15', type: 'Свободно', isShow:false},
        {time:'11:15 - 11:30', type: 'Свободно', isShow:false},
        {time:'11:30 - 11:45', type: 'Свободно', isShow:false},
        {time:'11:45 - 12:00', type: 'Свободно', isShow:false},
        {time:'12:00 - 12:15', type: 'Свободно', isShow:false},
        {time:'12:15 - 12:30', type: 'Свободно', isShow:false},
        {time:'12:30 - 12:45', type: 'Свободно', isShow:false},
        {time:'12:45 - 13:00', type: 'Свободно', isShow:false},
        {time:'13:00 - 13:15', type: 'Свободно', isShow:false},
        {time:'13:15 - 13:30', type: 'Свободно', isShow:false},
        {time:'13:30 - 13:45', type: 'Свободно', isShow:false},
        {time:'13:45 - 14:00', type: 'Свободно', isShow:false},
        {time:'14:00 - 14:15', type: 'Свободно', isShow:false},
        {time:'14:15 - 14:30', type: 'Свободно', isShow:false},
        {time:'14:30 - 14:45', type: 'Свободно', isShow:false},
        {time:'14:45 - 15:00', type: 'Свободно', isShow:false},
        {time:'15:00 - 15:15', type: 'Свободно', isShow:false},
        {time:'15:15 - 15:30', type: 'Свободно', isShow:false},
        {time:'15:30 - 15:45', type: 'Свободно', isShow:false},
        {time:'15:45 - 16:00', type: 'Свободно', isShow:false},
        {time:'16:00 - 16:15', type: 'Занят', isShow:false, duration:15},
        {time:'16:15 - 16:30', type: 'Занят', isShow:false, duration:15},
        {time:'16:30 - 16:45', type: 'Занят', isShow:false, duration:15},
        {time:'16:45 - 17:00', type: 'Занят', isShow:false,duration:15},
        {time:'17:00 - 17:15', type: 'Свободно', isShow:false},
        {time:'17:15 - 17:30', type: 'Свободно', isShow:false},
        {time:'17:30 - 17:45', type: 'Свободно', isShow:false},
        {time:'17:45 - 18:00', type: 'Свободно', isShow:false},
      ]
    }
  },
  methods:{
    showSchedule(obj){
      const filtered = this.schedule.filter((el)=>el.type === "Занят" && el.isShow)
      this.schedule.map((item)=>{
      if(item === obj){
          item.isShow = !item.isShow;
          filtered.map((num)=>{
            if(num - item.id === 1 || num - item.id === -1 ){
              item.duration+=15
            }
          })
        }
      })
      
    }
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
