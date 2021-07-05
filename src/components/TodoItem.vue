<template>
  <div class="todo-item" :class="{'is-complete':todo.completed}">
    <p>
      <input type="checkbox" :checked="todo.completed" @change="markComplete" >
      {{todo.title}}
      <button class="del" @click="$emit('del-todo', todo.id)" >x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    todo: {
      type: Object,
      default: () => ({})
    }
  },
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #cccccc dotted;
}

.is-complete {
  text-decoration: line-through;
}

.del {
  background: red;
  color: #FFF;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>