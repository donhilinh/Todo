<template>
  <div id="app">
    <ToDoItem
      v-bind:list_data_Todo="list_data_Todo"
      v-on:remove= "removeTodo"
      v-bind:color = "color"
    />
    <b-input-group class="mt-3">
      <b-form-input
        v-model="newTodoText"
        v-on:keyup.enter="addNewTodo"
        placeholder="Thêm Todo"
      ></b-form-input>
      <b-input-group-append>
        <b-button variant="info">Add</b-button>
      </b-input-group-append>
    </b-input-group>
    <Test1 />
  </div>
</template>

<script>
import ToDoItem from "./components/ToDoItem.vue";
import Test1 from "./components/Test1.vue";

export default {
  name: "app",
  components: {
    ToDoItem,
    Test1
  },
  data() {
    return {
      newTodoText: '',
      list_data_Todo: [
        { content: "item1" },
        { content: "item2" },
        { content: "item3" },
        { content: "item4" }
      ],
      color:"#fff"
    };
  },
  methods: {
    addNewTodo: function () {
      this.list_data_Todo.push({
        content: this.newTodoText
      })
      this.newTodoText = ''
    },
    removeTodo: function (index) {
      this.list_data_Todo.splice(index, 1)
    },
    
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  width: 400px;
}
</style>
