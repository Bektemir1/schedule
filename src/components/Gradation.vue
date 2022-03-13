<template>
 <div v-show="grad.isShow && grad.type==='Занят'" class="gradation" v-for="grad in gradation" :key="grad">
  <h2 class="gradation-title">Градация</h2>
  <p class="gradation-p">Длительность: <span>00:{{grad.duration}}</span></p>
 </div>
</template>

<script>

export default {
  name: 'Gradation',
  props:['gradation']
 
}
</script>

<style scoped>

.gradation{
    border:1px solid #616cf5;
    border-radius:5px;
    padding:15px;
    background: #f0f2ff;
    margin-bottom: 10px;
}
.gradation-title{
    font-size:20px;
    color:#616cf5;
}
.gradation-p{
    margin-bottom: 0;
    color:#999;
    font-size:14px;
}
.gradation-p span{
    font-weight:600;
    color:#333;

}
</style>
