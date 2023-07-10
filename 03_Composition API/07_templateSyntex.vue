<template>
    <div>
        <h2>템플릿 문법 -마크업 부분에 프로그래밍 요소 삽입</h2>

        <div class="box">
            <h3>이중 중괄호(콧수염 괄호)</h3>
            <div class="description">v-once :데이타가 변경되어도 갱신(반응)되지 않는 일회성으로 만들어줌</div>
            <p>{{ message }}</p>
            <p v-once>{{ message }}</p>
            <button v-on:click="message = message + '🧡'">Click</button>
        </div>
    </div>

    <div class="box">

        <h3>HTML (v-html)</h3>
        <div class="description">-이중 중괄호는 데이터를 HTML이 아닌 일반 텍스트로 해석. 실제 HTML을 사용하려면 v-html디렉티브 사용</div>
        <p>{{ rawHtml }}</p>
        <p v-html='rawHtml'></p>
        <p>{{ rawHtml2 }}</p>
        <p v-html="rawHtml2"></p>
    </div>
    <div class="box">
        <h3>속성(attribute) 바인딩</h3>
        <div class="description">이중중괄호는 HTML속성(attribute)에는 사용할 수 없다 -> 그래서 v-bind 사용</div>
        <p :title="gimoring">{{dynamitTitle}}</p>
        <input type="text" value="입력창 활성화 해줘" :disabled="isInputDisabled">
        <button @:click=" funcDisabled">활성화 하기</button>
        <br/>
        <input :="attrs">
    </div>
</template>

<script>
import { ref } from 'vue';

export default {
    setup() {
        const message = ref('안녕~~');
        const rawHtml = ref('<strong>비오는 아침</strong>')
        const rawHtml2 = '<span style="color:red">빨간 글씨!!!!!!!!!</span>'

        const dynamitTitle =  ref('마우스 올려라')
        const gimoring =  ref('기뭐링~')
        const isInputDisabled = ref(true);
        const funcDisabled = () => {
            isInputDisabled.value = !isInputDisabled.value
        }

        const attrs = ref({
            type : "text",
            placeholder : "다중 속성 바인드",
            value:'123456789',
            disabled: false
        })


        return { message, rawHtml, rawHtml2, dynamitTitle, gimoring, isInputDisabled, funcDisabled, attrs }
    }
}
</script>

<style scoped>
.box {
    border: 1px solid lightgrey;
    margin: 50px 10px;
    padding: 0 20px 20px;
}

p {
    margin: 3px;
}

.description {
    padding-bottom: 10px;
    color: #888;
    font-size: 14px
}</style>