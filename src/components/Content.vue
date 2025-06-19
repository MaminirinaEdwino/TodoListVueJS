<script setup>
import { ref } from 'vue';
import NewTodo from './NewTodo.vue';
let todoList = ref([
  
])
const deleteTodo = (id) => {
  todoList.value = todoList.value.filter(todo => todo.id !== id);
}
</script>
<template>
    <NewTodo :todo-list="todoList">

    </NewTodo>
    <div v-for="todo in todoList" class="todo-list">
        <div :key="todo.id" class="todo-item">
            
            <p :class="{ completed: todo.completed }">{{ todo.text }}</p> 
            <button class="completebtn"><label :for="`todo-${todo.id}`">
                <span v-if="todo.completed">Cancel</span>
                <span v-else>
                    Complete
                </span>
            </label></button>
            <input type="checkbox" v-model="todo.completed" :id="`todo-${todo.id}`" />
            <button class="deletebtn" @click="deleteTodo(todo.id)">Delete</button>
        </div>
    </div>
    <div v-if="todoList.length === 0" class="todo-list">
        <p>No todos available.</p></div>
    
</template>

<style scoped>
input[type="checkbox"] {
   display: none;
}
.todo-list{
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 20px;
    margin-bottom: 50px;
}
.todo-item{
    display: grid;
    grid-template-columns: 5fr 1fr 1fr;
    justify-content: left;
    min-width: 90%;
    max-width: 90%;
    padding: 10px;
    border: 2px solid #42b983;
    border-radius: 10px;
}
.todo-item button{
    min-width: 150px;
    max-width: 150px;
    height: 2rem;
    margin: 0.1rem;
    border: none;
    border-radius: 5px;
}
.completebtn{
    background-color: #42b983;
    color: white;
}
.deletebtn{
    background-color: red;
    color: white;
}
.completed {
    text-decoration: line-through;
    color: gray;
}
</style>