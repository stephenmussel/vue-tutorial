<script>

    // a child can accept input from the parent via props, but needs to declare the props it accepts 
    export default {
        props: {
            msg: String
        }
    }

</script>

<template>
    <h1>{{ msg }}</h1>
</template>