<script>
  let id = 0;

  // NOTES: inside <script>
  import ChildComp from './components/ChildComp.vue'

  export default {
    // component options
    components: {
      ChildComp
    },

    // data component option is a function that renders an object
    data() {
      return {
        greeting: 'Hello from parent'
        message: 'Hellow World!',
        counter: {
          count: 0
        },
        titleClass: 'title',
        text: '',
        awesome: true,
        newTodo: '',
        hideCompleted: false,
        todos: [
          { id: id++, text: 'Learn HTML', done: true },
          { id: id++, text: 'Learn JavaScript', done: true },
          { id: id++, text: 'Learn Vue', done: false }
        ],
        todoId: 1,
        todoData: null
      }
    },
    computed: {
      filteredTodos() {

        // click button either filters and hides todos that are completed or displays all todos 
        return this.hideCompleted ? this.todos.filter(each => !each.done) : this.todos
      }
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
      },
      async fetchData() {
        this.todoData = null
        const res = await fetch(
          `https://jsonplaceholder.typicode.com/todos/${this.todoId}`
        )
        this.todoData = await res.json()
      }
    },
    mounted() {
      // direct DOM operation to change `textContent`
      // this.$refs.p.textContent = 'mounted!'

      this.fetchData()
    },
    watch: {

      // function that watches for todoId to change then fetches data for new Id
      todoId() {
        this.fetchData()
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

  <!-- <form @submit.prevent="addToDo">
    <input v-model="newTodo" />
    <button>Add Todo</button>
  </form>
  <ul> -->

    <!-- list todo items -->
    <!-- <li v-for="todo in filteredTodos" :key="todo.id">
    <input type="checkbox" v-model="todo.done"/> -->

      <!-- renders styling by class if box is checked -->
      <!-- <span :class="{ done: todo.done }">{{ todo.text }}</span>
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul> -->

  <!-- toggles boolean value of hideCompleted -->
  <!-- <button @click="hideCompleted = !hideCompleted"> -->

    <!-- displays button text based on boolean  -->
    <!-- {{ hideCompleted ? 'Show all' : 'Hide completed'}}
  </button> -->

  <!-- <p ref="p">hello</p> -->

  <!-- <p>Todo id: {{ todoId }}</p>
  <button @click="todoId++">Fetch next todo</button>
  <p v-if="!todoData">Loading...</p>
  <pre v-else>{{ todoData }}</pre> -->

  <!-- render child component -->
  <ChildComp />

</template>

<style>

  .title {
    color: red;
  }

  .done {
    text-decoration: line-through;
  }

</style>