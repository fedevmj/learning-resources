<template>
    <TheHeader />

    <!-- 탭 기능 만들면서 TheResource로 이동 -->
    <!-- <StoredResources :resourceStored="storeResources" /> -->

    <TheResource />
</template>

<script>

    import TheHeader from '@/components/layouts/TheHeader.vue'
    import TheResource from '@/components/learning-resources/TheResource.vue'

    export default {
        components: {
            TheHeader,
            TheResource
        },
        setup() {
            
            return {
                // const storedResources 배열 -> TheResource.vue로 이동
                // storeResources,
                TheHeader,
                TheResource
            }
        }
    }
</script>

<style>
    @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+KR&display=swap');
    @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+KR&family=Work+Sans:wght@300&display=swap');
    * {
        box-sizing: border-box;
    }

    html, button {
        font-family: 'Noto Sans KR', 'Work Sans', sans-serif;    
        }

    body {
        margin: 0;
    }
</style>