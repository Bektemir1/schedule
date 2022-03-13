<template>
 <div :class="{busyBox: time.type === 'Занят' && time.isShow}"  @click="selectDate(time)" v-for="(time,index) in schedule.slice(0,schedule.length-1)" :key="time"  class="schedule d-flex justify-content-between">
     <div>{{time.date.getHours()}}:{{time.date.getMinutes()}}<span v-if="time.date.getMinutes() === 0">0</span> -
      <span v-if="index < 40">
          {{schedule[index+1].date.getHours()}}:{{schedule[index+1].date.getMinutes()}}<span v-if="schedule[index+1].date.getMinutes() === 0">0</span> 
      </span>
      
      </div>
     <div v-if="time.isShow" :class="{busy: time.type === 'Занят', free: time.type==='Свободно'}"> {{time.type}}</div> 
</div>
</template>

<script>

export default {
  name: 'Schedule',
  props:['schedule'],
  data(){
      return{
          selectedDate:{
              hour:'',
              min:'',
          }
      }
  },
  methods:{
        selectDate(time){
            let hour = time.date.getHours();
            let min = time.date.getMinutes();
            this.selectedDate.hour = hour,
            this.selectedDate.min = min,
            
            this.$emit('selectDate', this.selectedDate)


            
    }
},
    mounted(){
    
    }


}
</script>

<style scoped>
.free,.busy{
    font-size:14px;
}
.free{
    color: #5cbd85;
}
.busy{
    color:red;
}
.busyBox{
    background: #e8e8e8;
}

</style>
