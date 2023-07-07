<template>
    <div>
        <p>{{ message.value }}</p>
        <button v-on:click="addMessage">addClick</button>
        <hr/>
        <p>{{message2}}</p>
        <button v-on:click="addMessage2">addClick</button>
        <p>
            ref( ) = reference, 변이 가능한 값을 반환, value 속성을 포함<br/>
            - 템플릿에서 사용할때는 value는 빼줌, 내부값(value)이 Unwrapping
        </p>
    </div>
</template>

<script>
import { reactive, ref } from 'vue';

export default {
    setup() {
        let message = reactive({
            value: 'Hello Vue!'
        })
        const addMessage = () => {
            message.value = message.value + 'Vue는 할만하다';
        }
        const message2 = ref('안녕 Vue?') // ref (넘버, 스트링, 블린...)
        const addMessage2 = () => {
            message2.value = message2.value + '!';
        }

        return {
            message,
            addMessage,
            message2,
            addMessage2
        }
    }
}
</script>

<style lang="scss" scoped></style>