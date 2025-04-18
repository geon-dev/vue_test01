<template>
  <div class="container">
    <h2>To-do List</h2>

    <TodoSimpleForm @add-todo="getChild" />

    {{ todoList }}
    <div style="color:red;" v-show="toggle">
      빈값
    </div>

    <TodoList :items="todoList" 
    @toggleTodo="getToggleTodo" 
    @delete-toto="deleteTodo" 
    @check-data="checkData"
    />
  </div>
</template>

<script setup>
import { ref } from "vue";
import TodoSimpleForm from './components/TodoSimpleForm.vue'
import TodoList from "./components/TodoList.vue";

const todo = ref('');
const todoList = ref([
  {
    id: Date.now(),
    subject: 'abc',
    completed: false,
  }
]);  // 빈 배열로 초기화

const toggle = ref(false);

const todoStyle = {
  textDecoration: 'line-through',
  color: 'gray'
}

const getChild = (data) => {
  todoList.value.push(data);
};

const getToggleTodo = (data) => {
  todoList.value[data].completed = !todoList.value[data].completed;
};

const deleteTodo = (index) => {
  todoList.value.splice(index, 1);
};

const checkData =(data) => {
  console.log('parent > ', data);
};

</script>

<style lang="scss" scoped></style>