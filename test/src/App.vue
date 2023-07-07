<template>
    <div>
        <h2>Computed - 계산된 속성</h2>
        - 템플릿 문법이 길어지면 가독성이 떨어지고, 유지보수가 어려워지는 것을 방지<br />
        - 계산한 것을 캐싱해주고, 그것을 호출함, 데이터가 변경될 때 다시 계산해줌
        <div class="box">
            <h3>{{ lunch.name }}</h3>
            <p>엄마 점심은?</p>
            <p style="font-size: 28px; font-weight: 600; color: red;">{{ hasMenu }}</p>
            <p style="font-size: 28px; font-weight: 600; color: red;">{{ hasMenu }}</p>
            <p style="font-size: 28px; font-weight: 600; color: red;">{{ hasMenu }}</p>
            <p style="font-size: 28px; font-weight: 600; color: blue;">{{ exisMenu() }}</p>
            <p style="font-size: 28px; font-weight: 600; color: blue;">{{ exisMenu() }}</p>
            <p style="font-size: 28px; font-weight: 600; color: blue;">{{ exisMenu() }}</p>
            <button v-on:click="counter++" style="background: #333; color: #fff;">{{ counter }}</button>
            <hr />
            <p>{{ fullName }}</p>
        </div>
    </div>
</template>

<script>
import { computed, ref } from 'vue';

export default {
    setup() {
        const lunch = {
            name: '엄마가 해준 점심',
            menu: [
                '볶음밥',
                '닭갈비',
                '마라탕'
            ]
        }
        const hasMenu = computed(() => {
            console.log('computed');
            return lunch.menu.length > 0 ? '식탁와서 먹어라' : '엄마 힘들다';
        })

        const exisMenu = () => {
            console.log('일반 함수');
            return lunch.menu.length > 0 ? '식탁와서 먹어라' : '엄마 힘들다';
        }

        const counter = ref(0);

        const firstName = ref('홍');
        const lastName = ref('길동');
        // const fullName = computed(()=> firstName.value +' '+ lastName.value)
        const fullName = computed({
            get() {
                return firstName.value + ' ' + lastName.value
            },
            set(value) {
                console.log('value ', value);
                [firstName.value, lastName.value] = value.split(' ');
            }
        })

        console.log('수정 전-', fullName.value);
        fullName.value = '전 지현';
        console.log('수정 후-', fullName.value); //readonly 경고뜸


        return {
            lunch,
            hasMenu,
            exisMenu,
            counter,
            fullName
        }
    }
}
</script>

<style lang="scss" scoped></style>