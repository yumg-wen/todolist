<template>
<!-- form表單 -->
 <form class="form-inline " @submit.prevent="onFormSubmit">
  <div class="input-group mb-2 mr-sm-2">
    <!-- 輸入框前綴 -->
    <div class="input-group-prepend">
      <div class="input-group-text">任務</div>
    </div>
    <!-- 文字輸入框 -->
    <input type="text"   placeholder="請輸入任務" style="width:22.25rem;" v-model.trim="taskName">
     <!-- 添加按鈕 -->
     <button type="submit" class="btn btn-primary ml-6">添加新任務</button>
   
    
  </div>
  

  
</form>
</template>

<script>
export default {
name:"MyToDoInput",
emits:['add'],

data(){
  return{
    taskName:"",
  }
}
,
methods:{
  //表單提交事件處理函數
  onFormSubmit(){
    //若為空
    if(!this.taskName) return alert("任務不能為空")
    //有任務回傳任務資訊
    this.$emit('add',this.taskName)
    //回傳完任務，輸入框清空
    this.taskName=""
  }
}
}
</script>

<style lang="less" scoped>

</style>