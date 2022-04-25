<template>
    <button :type="type" :class="mode">
        <!--slot에 styling을 담아 전달하는 방식으로 아래의 props, 
        <style></style> 그리고 learningResource.vue 파일 참고  -->
        <slot></slot>
    </button>
</template>

<script>
    export default{
        props: ['type', 'mode']
    }
</script>

<style scoped>
    button {
        padding: 0.75rem 1.5rem;
        font-family: inherit;
        background-color: #3a0061;
        border: 1px solid #3a0061;
        color: white;
        cursor: pointer;
    }

    button:hover,
    button:active {
        background-color: #270041;
        border-color: #270041;
    }

    .flat {
        background-color: transparent;
        color: #3a0061;
        border: none;
    }

    .flat:hover,
    .flat:active {
        background-color: #edd2ff;
    }
</style>