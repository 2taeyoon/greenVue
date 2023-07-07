<template>
    <div>
        <p>author: {{ author }}</p>
        <p>year: {{ year }}</p>
        <p>title: {{ title }}</p>
        <p>description: {{ description }}</p>
        <p>price: {{ priceSpecial }}</p>
    </div>
</template>

<script>
import { reactive, /*toRef,*/ toRefs, readonly } from 'vue';

    export default {
        setup () {
            const book = reactive({
                author: 'Vue team',
                year: '2023',
                title: 'Vue 3 Guide',
                description: '초보자를 위한 Vue에 관한 모든것',
                price: '무료'
            })
            const { author, year, title, description, price } = toRefs(book);
            // const author = toRef(book, 'author'); // 한개씩 가져올 때
            // const year = toRef(book, 'year');
            // const title = toRef(book, 'title');
            // const description = toRef(book, 'description');
            // const price = toRef(book, 'price');
            // 구조분해할당 - 반응성을 잃어버림
            // toRefs를 이용하면 상태가 변경되어도 reactive 속성이 유지된다.
            console.log('typeof title', typeof title)

            book.title = 'Vue 3 Beginner';
            
            const priceSpecial = readonly(price);

            return {
                book, author, year, title, description,
                priceSpecial
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>