<template>
  <view class="container">
    <Statusbar color="#FFCE00" />
    <Header title="Mari´s app" />

    <view class="inputContainer">
      <text-input class="input" v-model="newTodoText" :placeholder="'To do task'" />
      <touchable-opacity class="add-btn" :on-press="newTodo">
        <text class="btn-text">ADD</text>
      </touchable-opacity>
    </view>

    <view class="todo" v-for="todo in todos" :key="todo.id">
      <touchable-opacity :on-press="() => toggleDone(todo.id)">
        <text class="todo-text done" v-if="todo.done">{{ todo.title }}</text>
        <text class="todo-text" v-else>{{ todo.title }}</text>
      </touchable-opacity>
      <touchable-opacity class="remove-btn" :on-press="() => removeTodo(todo.id)">
        <text class="remove-btn-text">Remove</text>
      </touchable-opacity>
    </view>

    <touchable-opacity :on-press="handleButton" :style="{backgroundColor: 'red', padding: 10}">
      <text class="btn-text">Switch Screen</text>
    </touchable-opacity>
  </view>
</template>

<script>
import Statusbar from '../components/Statusbar';
import Header from '../components/Header';

export default {
  props: {
    navigation: {
      type: Object
    }
  },
  data () {
    return {
      newTodoText: '',
      switch: '',
      todos: [
        {
          id: 0,
          title: 'Go for a walk',
          done: false
        },
        {
          id: 1,
          title: 'Drink a beer',
          done: false
        }
      ]
    }
  },
  components: {
    Statusbar,
    Header
  },
  methods: {
    newTodo () {
      this.todos.push({
        id: this.todos.length + 1,
        title: this.newTodoText,
        done: false
      });

      this.newTodoText = '';
    },
    toggleDone (id) {
      this.todos = this.todos.map(todo => {
        if (todo.id == id) todo.done = !todo.done;
        return todo;
      })
    },
    removeTodo (id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    handleButton() {
      this.navigation.navigate("Another");
    },
  }
}
</script>

<style>
.container {
  background-color: white;
  flex: 1;
}
.inputContainer {
  flex-direction: row;
  justify-content: center;
  align-items: stretch;
}
.input {
  flex: 1;
  height: 35px;
  background-color: #F3F3F3;
  font-size: 18px;
  color: #888888;
}
.add-btn {
  width: 100px;
  height: 35px;
  background-color: #FFCE00;
  justify-content: center;
  align-items: center;
}
.btn-text {
  font-size: 18px;
  font-weight: 700;
}
.todo {
  flex-direction: row;
  justify-content: space-between;
  padding: 15px;
}
.todo-text {
  font-size: 18px;
}
.done {
  color: #AAAAAA;
}
.remove-btn-text {
  font-size: 18px;
  color: red;
}
</style>
