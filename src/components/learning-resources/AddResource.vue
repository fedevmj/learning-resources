<template>

    <base-card>
        <form @submit.prevent="saveInfo">
            <div class="form-control">
                <label for="title">제목</label>
                <input id="title" name="title" type="text" v-model="title" @keyup="saveTitle">
            </div>

            <div class="form-control">
                <label for="description">상세설명</label>
                <textarea id="description" name="description" rows="3" v-model="description"
                    @keyup="saveDesc"></textarea>
            </div>

            <div class="form-control">
                <label for="link">링크주소</label>
                <input id="link" name="link" type="url" v-model="link" @keyup="saveLink">
            </div>

            <div class="form-control">
                <base-button type="submit">추가하기</base-button>
            </div>
        </form>
    </base-card>

    <base-dialog v-if="inputIsInvalid" title="오류">

        <template #default>
            <p>내용을 입력해 주세요.</p>
            <p>제목, 상세설명, 링크주소가 모두 필요합니다.</p>
        </template>
        
        <template #actions>
            <base-button @click="close">닫기</base-button>
        </template>

    </base-dialog>

</template>

<script>
    import {
        ref,
        getCurrentInstance
    } from 'vue';
    export default {
        emits: ['save-info'],
        setup() {
            const {
                emit
            } = getCurrentInstance();

            const inputIsInvalid = ref(false);

            const title = ref('');
            const saveTitle = (event) => {
                title.value = event.target.value;
            }

            const description = ref('');
            const saveDesc = (event) => {
                description.value = event.target.value;
            }

            const link = ref('');
            const saveLink = (event) => {
                link.value = event.target.value;
            }

            const saveInfo = () => {

                if (title.value !== '' && description.value !== '' && link.value !== '') {
                    inputIsInvalid.value = false;
                    emit('save-info', title.value, description.value, link.value)

                } else {
                    inputIsInvalid.value = true;
                    return;

                } 
            }


            const close = () => {
                inputIsInvalid.value = false;
            }

            return {
                saveTitle,
                saveDesc,
                saveLink,
                saveInfo,
                close,
                title,
                description,
                link,
                inputIsInvalid
            }
        }


    }
</script>

<style scoped>
    label {
        font-weight: bold;
        display: block;
        margin-bottom: 0.5rem;
    }

    input,
    textarea {
        display: block;
        width: 100%;
        font: inherit;
        padding: 0.15rem;
        border: 1px solid #ccc;
    }

    input:focus,
    textarea:focus {
        outline: none;
        border-color: #3a0061;
        background-color: #f7ebff;
    }

    .form-control {
        margin: 1rem 0;
    }
</style>