<template>
<div class="container">
  <h2>Todo List</h2>
  <div class="input-group" style="margin-bottom:10px;">
    <input type="text" class="form-control" placeholder="할일을 입력하세요"
    v-model="todo_text" v-on:keyup.enter="createtodo(todo_text)">
    <span class="input-group-btn">
      <button class="btn btn-success" type="button" @click="createtodo(todo_text)">추가</button>
    </span>
  </div>
  <ul class="list-group">
    <li class="list-group-item" v-for="(todo, index) in todos" :key=todo.name>
    {{todo.name}}
      <div class="btn-group pull-right" style="font-size: 12px; line-height: 1;">
        <button class="btn btn-xs btn-danger" type="button"
        @click="deletetodo(index)">삭제</button>
      </div>
    </li>
  </ul>
</div>
</template>

<script>
export default {
  name: 'TodoPage',
  data () {
    return {
      todos: [
        {
          name:'청소'
        },
        {
          name:'블로그 쓰기'
        },
        {
          name:'밥먹기'
        },
        {
          name:'안녕'
        }
      ]
    }
  },
  methods: {
    deletetodo(i) {
      this.todos.splice(i, 1);
    },
    createtodo(text) {
      if (text) {
        this.todos.push({name: text});
        this.todo_text = '';
      }
    }
  }
}
</script>
