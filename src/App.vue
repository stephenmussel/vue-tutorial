<script>
  export default {
    // component options

    // data component option is a function that renders an object
    data() {
      return {
        message: 'Hellow World!'
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
  <h1>{{ message.split('').reverse().join('') }}</h1>
</template>

