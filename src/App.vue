<script>
import { ref, toRefs, reactive, onMounted, computed } from "vue";
import TodoList from "./components/TodoList.vue";

export default {
  components: { TodoList },
  setup() {
    const todo = ref("");
    const todos = reactive({
      list: [],
    });

    onMounted(() => {
      todos.list = JSON.parse(localStorage.getItem("todos")) || [];
    });

    const countTodo = computed(() => {
      return todos.list.length;
    });

    const createTodo = () => {
      todos.list.unshift({
        activity: todo.value,
        status: false,
      });
      todo.value = "";
      saveToLocal();
    };

    const deleteTodo = (todoIndex) => {
      todos.list = todos.list.filter((todo, index) => {
        if (index != todoIndex) {
          return todo;
        }
      });
      saveToLocal();
    };

    const doneTodo = (todoIndex) => {
      todos.list = todos.list.map((todo, index) => {
        if (index == todoIndex) {
          todo.status = !todo.status;
        }
        return todo;
      });
      saveToLocal();
    };

    const saveToLocal = () => {
      localStorage.setItem("todos", JSON.stringify(todos.list));
    };

    return {
      todo,
      ...toRefs(todos),
      countTodo,
      createTodo,
      deleteTodo,
      doneTodo,
    };
  },
};
</script>

<template>
  <div class="container-fluid bg-light rounded-lg vh-100">
    <div class="row p-5 text-center">
      <div class="col">
        <h1 class="fw-bold">Simple Todo App</h1>
        <p class="text-muted">Developed using Vue 3 Composition API.</p>
      </div>
    </div>

    <div class="row justify-content-center">
      <div class="col-md-10 mb-3">
        <div class="d-flex gap-1 m-1">
          <input class="form-control" v-model="todo" @keyup.enter="createTodo" type="text" placeholder="Add new todo" />
          <button class="btn btn-primary" @click="createTodo">Add</button>
        </div>
      </div>

      <div class="col-md-10 mb-3">
        <div class="badge bg-info float-end m-1">Total: {{ countTodo }}</div>
      </div>

      <TodoList :todos="list" @parsingIndexDelete="deleteTodo" @parsingIndexDone="doneTodo" />
    </div>
  </div>
</template>
