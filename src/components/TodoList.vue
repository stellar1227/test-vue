<template>
  <ul>
      <li v-for="(todoItem , index) in propsdata" :key="todoItem" class="shadow">
          <i class="checkBtn fa fa-check" aria-hidden="true"></i>
          {{todoItem}}
          <span class="removeBtn" type="button" v-on:click="removeTodo(todoItem,index)">
              <i class="fa fa-trash-o" aria-hidden="true"></i>
          </span>
      </li>
  </ul>
</template>

<script>
export default {
    props : ['propsdata'],
    
    methods : {
        removeTodo(t, i){
           this.$emit('removeTodo', t, i)
        }
    }
}
</script>

<style>
ul{
    list-style-type:none;
    padding-left:0;
    margin-top:0;
    text-align:let;
}
li{
    display: flex;
    min-height:50px;
    height:50px;
    line-height:50px;
    margin:0.5rem 0;
    padding:0 0.9rem;
    background:white;
    border-radius:5px;
}
.checkBtn{
    line-height:45px;
    color:#62acde;
    margin-right:5px;
}
.removeBtn{
    margin-left:auto;
    color:#de4343;
}
</style>