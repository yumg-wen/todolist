<template>
<div class="btn-container mt-3">
 
  <button type="button" class="btn" :class="active===0?'btn-primary':'btn-secondary'"
  @click="onBtnClick(0)">全部</button>
  <button type="button" class="btn" :class="active===1?'btn-primary':'btn-secondary'"  @click='onBtnClick(1)' >已完成</button>
  <button type="button" class="btn" :class="active===2?'btn-primary':'btn-secondary'"  @click='onBtnClick(2)'>待完成</button>
</div>


</template>

<script>
export default {
  name:"MyButton",
  //聲明 v-model相關的自訂義屬性
  emits:['update:active'],
  props:{
    //激活項的索引值
   active:{
      type : Number,
      required:true,
      default:0
   }
 },
 methods:{
   //按鈕的點擊事件處理函數
   onBtnClick(index){
     //1.如果當前點擊按鈕的索引值=props傳遞過來的索引值，則沒必要觸發 update:active 自定義事件
     if(index===this.active) return
     //2.通過 this.$emit()方法觸發自定義事件
     this.$emit('update:active',index)

   }
 }
}
</script>

<style lang="less" scoped>
.btn-container{
  width: 25rem;
  text-align: center;
}
</style>