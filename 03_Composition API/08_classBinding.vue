<template>
    <div>
        <div :class="classObject" class="text">주식</div>
        <button @click="toggle">주가 하락</button>
        <button @click="hasWanning = !hasWanning">주가 상승</button>
    </div>
</template>

<script>
import { reactive, ref } from 'vue';

export default {
    setup () {
        const isActive = ref(false);
        const hasWanning = ref(false);
        const classObject = reactive({
            active: isActive, 'text-danger': hasWanning
        })

        const toggle = () => {
            isActive.value = !isActive.value
        }

        return { isActive, toggle, hasWanning, classObject }
    }
}
</script>

<style lang="scss" scoped>
    .active { color: blue; text-decoration: underline; font-weight: bold; }
    .text { font-size: 24px; }
    .text-danger { color: red; text-decoration: underline; font-weight: bold; }
</style>