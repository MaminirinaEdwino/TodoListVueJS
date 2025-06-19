<script setup>
import { ref } from 'vue';

const newTodoText = ref('');
// const emit = defineEmits(['add-todo']);
const props = defineProps(['todoList']);
const addTodo = ()=>{
    if (newTodoText.value.trim() === '') {
        return; // Prevent adding empty todos
    }
    const newTodo = {
        id: Date.now(), // Unique ID based on timestamp
        text: newTodoText.value,
        completed: false
    };
    props.todoList.push(newTodo); // Add the new todo to the list
    newTodoText.value = ''; // Clear the input field
}
</script>

<template>
    <div class="new-todo">
        <input type="text" v-model="newTodoText" placeholder="Add a new todo" @keyup.enter="addTodo" />
        <button @click="addTodo">Add Todo</button>
    </div>
</template>
<style scoped>
    .new-todo{
        padding: 2rem;
        display: flex;
        justify-content: center;
    }
    .new-todo input {
        width: 70%;
        padding: 0.5rem;
        border: 2px solid #42b983;
        border-radius: 5px;
        font-size: 1rem;
    }
    .new-todo button {
        padding: 0.5rem 1rem;
        margin-left: 10px;
        background-color: #42b983;
        color: white;
        border: none;
        border-radius: 5px;
        cursor: pointer;
        font-size: 1rem;
    }
</style>