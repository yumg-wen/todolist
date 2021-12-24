<template>
<div class="list-container mt-3">
  <ul class="list-group ">
  <!-- 列表框 -->
  <li class="list-group-item d-flex justify-content-between align-items-start" v-for="item in list" :key="item.id">
    
    <div class="form-check">
  <input class="form-check-input" type="checkbox" value="" :id="item.id" v-model="item.done">
  <label class="form-check-label" :class="item.done?'delete':''" :for="item.id">
   {{item.task}}
  </label>
</div>
    <!-- 標徽badge -->
    <span class="badge bg-success rounded-pill" v-if="item.done">完成</span>
    <span class="badge bg-warning rounded-pill" v-else>待完成</span>
  </li>
  
</ul>
</div>

</template>

<script>
export default {
  name:"MyTodoList",
  data(){
    return{
     
    }
  },
  props:{
   list:{
     type:Array,
     required:true,
     default:[]
   }
  }

}
</script>

<style lang="less" scoped>
.list-group{
  width: 25rem;
} 
.delete{
  color: gray;
  text-decoration: line-through;
  font-style:italic
}
</style>