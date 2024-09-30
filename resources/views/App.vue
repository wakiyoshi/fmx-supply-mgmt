<template>
    <div id="app">
        <h1>Welcome to Vue.js with Laravel!</h1>
        <example-component />
    </div>
</template>

<script>
import ExampleComponent from '../components/Example.vue';

export default {
    components: {
        ExampleComponent,
    },
};
</script>

<style scoped>
h1 {
    color: #42b983;
}
</style>

