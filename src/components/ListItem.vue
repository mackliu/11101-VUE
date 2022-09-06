<script setup>
import {ref,reactive} from 'vue'
defineProps({todo:Object})


const delTodo=(idx)=>{
  todos.splice(idx,1)
}
const editTodo=(idx)=>{
  console.log(items.value[idx].childNodes)
  items.value[idx].childNodes[0].innerHTML=`<input type='text' v-model=\"form.todo\" value="${items.value[idx].childNodes[0].innerText}">`
  items.value[idx].childNodes[1].innerHTML=`<input type='date' v-model=\"form.due\" value="${items.value[idx].childNodes[1].innerText}">`
  items.value[idx].childNodes[2].innerHTML=`
  <select name="type"  v-model="form.type">
    <option value="1">很重要</option>
    <option value="2">普通</option>
    <option value="3">不重要</option>
  </select>
  `
  let button=document.createElement('button')
  let node=document.createTextNode('OK');
  button.appendChild(node)

  items.value[idx].childNodes[3].remove()
  items.value[idx].childNodes[3].remove()
  items.value[idx].appendChild(button)
}
</script>
<template>

<div class="list-item">
    <div>{{ todo.todo }}</div>
    <div>{{ todo.due }}</div>
    <div>{{ todo.type }}</div>
    <button @click="editTodo(idx)">編輯</button>
    <button @click="delTodo(idx)">X</button>
  </div>

</template>
<style scoped>
.list-item{
  border:1px solid #999;
  display:flex;
  box-shadow: 0 0 3px #ccc;
  margin:0.5rem 2rem;
  padding:0.5rem;
  font-size:1.5rem
}
.list-item > div:nth-child(1){
  width:12rem;
}
.list-item > div:nth-child(2){
  width:10rem;
}
.list-item > div:nth-child(3){
  width:5rem;
}
</style>