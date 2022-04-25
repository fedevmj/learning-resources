<template>
    <header>
        <h1>Learning Resources</h1>
    </header>
</template>

<script>

    export default {
        props: ['title'],

        setup() {
            return{
                
            }
        }
    }
</script>

<style scoped>
    header {
        width: 100%;
        height: 5rem;
        background-color: #3a0ca3;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    header h1 {
        color: white;
        margin: 0;
    }
</style>