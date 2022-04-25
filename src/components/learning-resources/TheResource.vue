<template>
    <base-card>
        <!-- custom component (여기서는 base-button)에 props or event lister를 추가할 경우
        default값으로 해당 custom component의 root element로 전달된다 (BaseButton에 있는 Button)-->
        <base-button @click="setSelectedTab('StoredResources')">저장하기</base-button>
        <base-button @click="setSelectedTab('AddResource')">추가하기</base-button>
    </base-card>
    <component :is="selectedTab"></component>
</template>

<script>
    import StoredResources from './StoredResources.vue'
    import AddResource from './AddResource.vue'
    import {ref, provide} from 'vue'

    export default{
        components: {
            StoredResources,
            AddResource
        },
        setup(){
            const selectedTab = 'StoredResources';

            const setSelectedTab = (tab) => {
                selectedTab.value = tab;
            }
            const storeResources = ref([{
                    id: 'official',
                    title: 'Vue.js 공식 가이드',
                    description: 'Vue.js official guide',
                    link: 'https://vuejs.org'
                },
                {
                    id: 'google',
                    title: 'Google',
                    description: '개발자들이 사랑하는 검색엔진',
                    link: 'https://google.com'
                }
            ])
            provide ('storeResources', storeResources)
            return{
                selectedTab,
                setSelectedTab,
                storeResources
            }
        },
    }

</script>