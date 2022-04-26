<template>
    <li>
        <base-card>
            <header>
                <h3>{{ title }}</h3>
                <base-button mode="flat" @click="deleteInfo(id)">삭제</base-button>
            </header>

            <p>{{ description }}</p>
            <nav><a :href="link">View Resources</a></nav>
        </base-card>
    </li>
</template>

<script>
    import {inject} from 'vue'
    export default {
        // deleteInfo에서 id가 필요하니까 props로 받아오고 TheResource.vue에서 id를 :id="resource.id"로 연결해 줘야 한다.
        props: ['id', 'title', 'description', 'link'],
        setup() {
            const deleteInfo = inject('deleteInfo')
            return {
                deleteInfo
            }
        }
    }
</script>

<style scoped>
    li {
        margin: auto;
        max-width: 40rem;
    }

    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    h3 {
        font-size: 1.25rem;
        margin: 0.5rem 0;
    }

    p {
        margin: 0.5rem 0;
    }

    a {
        text-decoration: none;
        color: #ce5c00;
    }

    a:hover,
    a:active {
        color: #c89300;
    }
</style>