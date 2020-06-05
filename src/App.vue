<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <TodoList v-bind:propsdata="todoItems" @removeTodo="removeTodo"></TodoList>
    <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader';
import TodoInput from './components/TodoInput';
import TodoList from './components/TodoList';
import TodoFooter from './components/TodoFooter';

export default {
  data(){
    return {
      todoItems : []
    }
  },
  methods : {
    addTodo(t){
      localStorage.setItem(t,t);
      this.todoItems.push(t)
    },
    clearAll(){
      localStorage.clear();
      this.todoItems = [];
    },
    removeTodo(t, i){
        localStorage.removeItem(t);
        this.todoItems.splice(i, 1)
    }
  },
  created(){//bm, m에서 해도되지만 코드 개선시 문제가 생김 확인하자 
      if(localStorage.length > 0){
          for(var i = 0; i < localStorage.length; i++){
              this.todoItems.push(localStorage.key(i))
          }
      }
  },
  components : {
    'TodoHeader' : TodoHeader,
    'TodoInput' : TodoInput,
    'TodoList' : TodoList,
    'TodoFooter' : TodoFooter
  }
}
</script>

<style>
body{
    text-align:center;
    background-color:#f6f6f8
}
input{
  border-style:groove;
  width:200px;
}
button{
  border-style:groove;
}
.shadow{
  box-shadow:5px 10xp 10xp rgba(0,0,0,0.03)
}
</style>
