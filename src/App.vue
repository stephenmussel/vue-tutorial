<script>
  export default {
    // component options

    // data component option is a function that renders an object
    data() {
      return {
        message: 'Hellow World!',
        counter: {
          count: 0
        },
        titleClass: 'title'
      }
    },
    methods: {
      increment() {
        this.counter.count++
      },
      decrease() {
        this.counter.count--
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
  <button @click="increment">Add to Count: {{ counter.count }}</button>&nbsp;
  <!-- decrease count w/shorthand -->
  <button @click="decrease">Decrease Count: {{ counter.count }}</button>

</template>

<style>

  .title {
    color: red;
  }

</style>