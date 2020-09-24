<template>
  <div>
    <input v-model="text" class="border" type="text" />
    <button @click="addTodo(text)">add</button>
    <div>
      <div
        v-for="(todo, index) in todos"
        :key="index"
        class="w-4/5 flex justify-between"
      >
        <p>{{ todo }}</p>
        <button @click="deleteTodo(index)">delete</button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref } from 'vue';

export default defineComponent({
  setup() {
    const todos: string[] = reactive([]);
    const text = ref('');
    const addTodo = (todo: string) => {
      todos.push(todo);
    };
    const deleteTodo = (index: number) => {
      todos.splice(index, 1);
    };
    return { todos, text, deleteTodo, addTodo };
  },
});
</script>
