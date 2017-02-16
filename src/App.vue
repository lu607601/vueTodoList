<template>
  <div id="app">
    <h2>TodoList</h2>
    <input class="addInput" type="text" name="" v-model="newItem" v-on:keydown.enter="addItem">
    <ul>
      <todo v-for="(label, index) in items" :label=label :index=index @delete="deleteItem"> </todo>
    </ul>
  </div>
</template>

<script>
import Todo from 'components/Todo'
export default {
  name: 'app',
  data () {
    return {
      newItem: '',
      items: ['aaa']
    }
  },
  components: {
    Todo
  },
  methods: {
    addItem: function () {
      this.items.push(this.newItem)
      this.newItem = ''
    },
    deleteItem: function (index) {
      this.items.splice(index, 1)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
  width: 700px;
  margin: 30px auto;
}
ul {
  list-style-type: none;
  padding: 0;
}
.addInput {
  width: 600px;
  height: 36px;
}
</style>
