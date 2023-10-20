<script >
export default {

  data() {
    return {
      count: 0,
      todoList: [],
      todo: ""
    }
  },

  methods: {
    increment() {
      this.count++;
    },

    addTodo() {
      this.todoList.push({ task: this.todo, complete: false })
    },

    removeTodo(index) {
      this.todoList.splice(index, 1)
    }


  }

}
</script>

<template>
  <div id="#todo">
    <h1>Todo List</h1>
    <div>
      <input type="text" v-model="todo" @keyup.enter="addTodo">
      <button @click="addTodo">Add</button>
    </div>
    <ul>
      <li v-for="(todo, index) in todoList" :key="index" :class="{ 'completed-task': todo.complete }">
        <div class="task-item">
          <div class="task-detail"> 
            <input type="checkbox" v-model="todo.complete">
            {{ todo.task }}
          </div>
          <button @click="removeTodo(index)">X</button>
        </div>

      </li>
    </ul>
  </div>
</template>

<style scoped>
#todo {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

h1 {
  font-size: 24px;
  margin-bottom: 20px;
}

input[type="text"] {
  width: 70%;
  padding: 8px;
  margin-right: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  padding: 8px 16px;
  background-color: #007BFF;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px 0;
  border-bottom: 1px solid #ccc;
  margin: 5px;
  padding: 5px;
}

button.remove-button {
  background-color: #FF5555;
}

.completed-task {
  background-color: #C1FFB8;
  color: #333;
}

.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px 0;
  width: 100%;
}

.task-item button {
  padding: 8px 16px;
  background-color: #FF5555;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.task-item input[type="checkbox"] {
  width: 20px;
  height: 20px;
  margin-right: 10px;
}
.task-detail{
  display: flex;
    justify-content: center;
    align-items: center;
}
</style>
