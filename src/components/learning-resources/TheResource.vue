<template>

    <base-card>
        <!-- custom component (여기서는 base-button)에 props or event lister를 추가할 경우
        default값으로 해당 custom component의 root element로 전달된다 (BaseButton에 있는 Button)-->
        <base-button @click="setSelectedTab('StoredResources')" :mode='storedResButtonMode'>저장하기</base-button>
        <base-button @click="setSelectedTab('AddResource')" :mode='addResButtonMode'>추가하기</base-button>
    </base-card>
    <!-- <keep-alive> -->
        <component :is="selectedTab" @save-info="saveInfo"></component>
    <!-- </keep-alive> -->
</template>

<script>
    import StoredResources from './StoredResources.vue'
    import AddResource from './AddResource.vue'
    import {ref, provide, computed} from 'vue'

    export default{
        components: {
            StoredResources,
            AddResource
        },
        setup(){
            const selectedTab = ref('StoredResources');

            const setSelectedTab = (tab) => {
                selectedTab.value = tab;
            }

            const storedResButtonMode = computed(() => {
                return selectedTab.value === 'StoredResources' ? null : 'flat'
            });

            const addResButtonMode = computed(() => {
                return selectedTab.value === 'AddResource' ? null : 'flat'
            });
            
            const storeResources = ref([
                {
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

            const saveInfo = (_title, _desc, _link) => {
                const newInfo = {
                    id : new Date().toISOString(),
                    title : _title,
                    description : _desc,
                    link : _link
                };

                // unshift: push와 같으며 목록 제일 위에 데이터를 저장.
                storeResources.value.unshift(newInfo)
                // 저장 후 목록 화면 보여주기
                selectedTab.value = 'StoredResources';

                console.log(storeResources)
            }


            provide ('storeResources', storeResources)
            return{
                selectedTab,
                setSelectedTab,
                storeResources,
                storedResButtonMode,
                addResButtonMode,
                saveInfo,
            }
        }
    }


</script>