<template>
    <div class="box">
        <h2>watch</h2>
        <p class="description">Reactivity 데이타 상태가 변경되었을때를 감지하여 다른 작업을 수행</p>
        <code>
            watch(감지할 반응형 데이타, 콜백함수)<br>
            watch(감지할 반응형 데이타(함수), (새로운값, 기존값)=>{ })<br>
        </code>
    </div>
</template>

<script>
import { reactive, ref, watch } from 'vue';

export default {
    setup() {
        const message = ref('Hellow World!!');

        watch(message, (newValue, oldValue) => {
            console.log('newValue: ', newValue);
            console.log('oldValue: ', oldValue);
        })

        const x = ref(0);
        const y = ref(0);

        //x,y합계값을 감지
        watch(() => x.value + y.value, (sum, oldSum) => {
            console.log('sum: ', sum)
            console.log('oldSum: ', oldSum)
        })

        //따로따로 감지할 수도 있음
        watch([x, y], ([newX, newY]) => {
            console.log('x,y를 동시에: ', newX, newY)
        });

        const hotel = reactive({
            name: 'shilla',
            emptyRooms: 45
        })
        //console.log('typeof hotel.emptyRooms?  ', typeof hotel.emptyRooms)

        watch(() => hotel.emptyRooms, (newValue, oldValue) => {
            console.log('hotel.enptyRooms: ', newValue)
            console.log('이전의 빈방: ', oldValue)
        })


        return { message, x, y, hotel }
    }
}
</script>

<style>
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