<template>
  <h1>Todo List</h1>
  <TodoInput @add=onAddNewTask ></TodoInput>
  <TodoList :list="taskList" ></TodoList>
  <ToDoButton v-model:active="activeBtnIndex"></ToDoButton>
</template>

<script>
import TodoList from "./components/todoList/todoList.vue"
import TodoInput from './components/todo-input/todo-input.vue'
import ToDoButton from "./components/todoButton/todoButton.vue";
export default {
  name:"MyApp",
  data(){
    return{
       todoList:[
     {id:1,task:"周一九點開會",done:true},
     {id:2,task:"週一晚上聚會",done:false},
     {id:3,task:"準備週三簡報",done:false}
     ],
      nextId:4,
      activeBtnIndex:0
    }
  },
 
  methods:{
    //TodoInput組件ad事件的處理函數
    onAddNewTask(taskName){
      // //向任務列表中新增任務信息
     this.todoList.push({
       id:this.nextId,
       task:taskName,
       done:false
     })
     this.nextId++

    }
  },
  computed:{
    taskList(){
      switch(this. activeBtnIndex){
        case 0:
          return this.todoList
          case 1:
            return this. todoList.filter(x=>x.done===true)
          case 2:
            return this. todoList.filter(x=>x.done!==true)
      }
    }
  },
  components:{
    TodoList,
   TodoInput,
   ToDoButton
  }

}
</script>

<style lang="less" scoped>

</style>
