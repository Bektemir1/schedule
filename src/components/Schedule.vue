<template>
 <div v-on:click="$emit('showSchedule', item)" :class="{busyBox: item.type === 'Занят' && item.isShow}" v-for="item in schedule" :key="item" class="schedule d-flex justify-content-between">
     <div>{{item.time}}</div>
     <div v-if="item.isShow" :class="{busy: item.type==='Занят', free: item.type === 'Свободно'}">{{item.type}}</div> 
</div>
</template>

<script>

export default {
  name: 'Schedule',
  props:['schedule'],
  emits:['showSchedule'],
 

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
