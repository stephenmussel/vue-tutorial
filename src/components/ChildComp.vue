<script>

    // a child can accept input from the parent via props, but needs to declare the props it accepts 
    export default {
        data() {
            return {
                title: 'Child component'
            }
        },
        props: {
            msg: String
        },
        emits: ['response'],
        created() {
            // emit with argument
            this.$emit('response', 'hello from child!')
        },
    }

</script>

<template>
    <h1>{{ title }}</h1>
</template>