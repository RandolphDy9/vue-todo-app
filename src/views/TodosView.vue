<script setup>
import { ref, computed } from "vue";
import { uid } from "uid";
import TodoCreator from "../components/TodoCreator.vue";
import TodoItem from "../components/TodoItem.vue";
import { Icon } from "@iconify/vue";

const toDoList = ref([]);

// watch(toDoList, () => {
//   setTodoListLocalStorage();
// }, {
//   deep: true
// })

const todoCompleted = computed(() => {
  return toDoList.value.length > 0 && toDoList.value.every((todo) => todo.isCompleted);
})

// const fetchTodoList = () => {
//   const savedTodoList = JSON.parse(localStorage.getItem("todoList"));
//   if (savedTodoList) {
//     toDoList.value = savedTodoList;
//   }
// }

// fetchTodoList();

// const setTodoListLocalStorage = () => {
//   localStorage.setItem("todoList", JSON.stringify(toDoList))
// }

const createTodo = (todo) => {
  toDoList.value.push({
    id: uid(),
    todo,
    isCompleted: null,
    isEditing: null
  });
}

const toggleComplete = (index) => {
  toDoList.value[index].isCompleted = !toDoList.value[index].isCompleted;
}

const updateTodo = (index) => {
  toDoList.value[index].isEditing = !toDoList.value[index].isEditing;
}

const updateTodoValue = (todoValue, index) => {
  toDoList.value[index].todo = todoValue;
}

const deleteTodo = (todoId) => {
  toDoList.value = toDoList.value.filter((item) => item.id !== todoId);
}

</script>

<template>
  <main>
    <h1>Create Todo</h1>
    <TodoCreator @create-todo="createTodo" />
    <ul class="todo-list" v-if="toDoList.length > 0">
      <TodoItem v-for="(todo, index) in toDoList" :todo="todo" :index="index" @toggle-complete="toggleComplete" @edit-todo="updateTodo" @delete-todo="deleteTodo"  @update-todo="updateTodoValue"  />
    </ul>
    <div class="todos-msg" v-else>
      <Icon icon="noto-v1:sad-but-relieved-face" width="22" />
      <span>You have no Todos to complete! Add one!</span>
    </div>
    <p v-if="todoCompleted" class="todos-msg">
      <Icon icon="noto-v1:party-popper" />
      <span>You have completed all Todos!</span>
    </p>
  </main>
</template>

<style lang="scss" scoped>
main {
  display: flex;
  flex-direction: column;
  max-width: 500px;
  width: 100%;
  margin: 0 auto;
  padding: 40px 16px;

  h1 {
    margin-bottom: 16px;
    text-align: center;
  }

  .todo-list {
    display: flex;
    flex-direction: column;
    list-style: none;
    margin-top: 24px;
    gap: 20px;
  }

  .todos-msg {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    margin-top: 24px;
  }
}
</style>
