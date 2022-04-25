<template>
    <ul>
        <LearningResource 
        v-for="resource in storeResources" 
        :key="resource.id" 
        :title="resource.title"
        :description="resource.description" 
        :link="resource.link" />
    </ul>
</template>

<script>
    import LearningResource from '@/components/learning-resources/LearningResource.vue'
    import {inject} from 'vue'
    export default {
        components: {
            LearningResource
        },
        // inject가 props를 대신함. provide는 TheResource.vue
        // props: ['resourceStored'],
        setup() {
            const storeResources = inject('storeResources');
            return {
                LearningResource,
                storeResources
            }
        }
    }
</script>

<style scoped>
    ul {
        list-style: none;
        margin: 0;
        padding: 0;
        margin: auto;
        max-width: 40rem;
    }
</style>