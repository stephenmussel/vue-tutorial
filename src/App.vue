<script>
  let id = 0;

  export default {
    // component options

    // data component option is a function that renders an object
    data() {
      return {
        message: 'Hellow World!',
        counter: {
          count: 0
        },
        titleClass: 'title',
        text: '',
        awesome: true,
        newTodo: '',
        todos: [
          { id: id++, text: 'Learn HTML', done: true },
          { id: id++, text: 'Learn JavaScript', done: true },
          { id: id++, text: 'Learn Vue', done: false }
        ]
      }
    },
    computed: {
      // ...
    },
    methods: {
      increment() {
        this.counter.count++
      },
      decrease() {
        this.counter.count--
      },
      // onInput(e) {
      //   this.text = e.target.value
      // }
      toggle() {
        this.awesome = !this.awesome
      },
      addToDo() {
        // adds todo to todos array
        this.todos.push({ id: id++, text: this.newTodo, done: false })
        this.newTodo = ''
      },
      removeTodo(todo) {
         // removes selected todo
        this.todos = this.todos.filter((selected) => selected !== todo)        
      }
    }
  }
</script>

<template>
  <!-- hard coded -->
  <!-- <h1>Hello World!</h1> -->

  <!-- how to render dynamic text based on value of `message` -->
  <!-- <h1>{{ message }}</h1> -->

  <!-- can use JS expressions -->
  <!-- <h1>{{ message.split('').reverse().join('') }}</h1> -->
  <!-- <p>Counter is: {{ counter.count }}</p> -->

  <!-- added dynamic class binding to `class` -->
  <!-- <h1 v-bind:class="titleClass">Make me red</h1> -->
  <!-- binding directive shorthand -->
  <!-- <h1 :class="titleClass">Make me red using bind shorthand!</h1> -->

  <!-- increments count -->
  <!-- <button v-on:click="increment">Count is: {{ counter.count }}</button>&nbsp; -->
  <!-- increments count w/shorthand -->
  <!-- <button @click="increment">Add to Count: {{ counter.count }}</button>&nbsp; -->
  <!-- decrease count w/shorthand -->
  <!-- <button @click="decrease">Decrease Count: {{ counter.count }}</button> -->

  <!-- <input :value="text" @input="onInput" placeholder="Type here" /> -->
  <!-- <input v-model="text" placeholder="Type here" /> -->
  <!-- <p>{{ text }}</p> -->

  <!-- <button @click="toggle">toggle</button>
  <h1 v-if="awesome">Vue is awesome!</h1>
  <h1 v-else>Oh no...</h1> -->

  <form @submit.prevent="addToDo">
    <input v-model="newTodo" />
    <button>Add Todo</button>
  </form>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
    <input type="checkbox" v-model="todo.done"/>
      <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
  <button @click="hideCompleted = !hideCompleted">
    {{ hideCompleted ? 'Show all' : 'Hide completed'}}
  </button>

</template>

<style>

  .title {
    color: red;
  }

  .done {
    text-decoration: line-through;
  }

</style>