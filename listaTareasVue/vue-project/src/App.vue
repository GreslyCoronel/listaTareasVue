<script setup>
import TaskComponent from '@/components/TaskComponent.vue';
import { ref } from 'vue';
let newTask 

const taskList = ref ([
  'Levantarse',
  'Cruzar el semáforo sin mirar',
  'Murio'
])

const addTask = ()=>{
  taskList.value.push(newTask)
  newTask=''
}

const deleteFromArray = (index=>{
  taskList.value.splice(index, 1)
  console.log('Kill', taskList)
})


</script>

<template>
<div class="px-4 py-3 mx-auto mt-12 space-y-2 overflow-hidden rounded shadow-md bg-gray-100 w-96 ">
  <h1 class="text-2xl font-semibold">Lista de tareas</h1>
  <div class="flex">
    <input type="text" class="w-4/5 h-8 px-2 py-1 border border-r-0 border-green-600 rounded rounded-r-none" v-model="newTask">
    <span class="w-1/5 h-8 text-xl font-bold text-center text-white bg-green-600 border-1-0 rounded rounded-l-none leading-0 
    hover:bg-green-700 hover:cursor-pointer" @click="addTask">
      +
    </span>
  </div>

  <TaskComponent v-for="(task, index) in taskList" :key="index" :name="task" :index="index" @emitDeleteTask="deleteFromArray"/>

</div>
</template>

<style scoped>

</style>
