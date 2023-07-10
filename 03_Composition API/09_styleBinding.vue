<template>
    <div>
        <div :style="styleObject">Lorem ipsum dolor sit amet consectetur adipisicing elit. Ex blanditiis animi eligendi aperiam aut in optio sint vel assumenda, iste facere provident cupiditate eos amet! Tempore quibusdam tempora quia quis.</div>
        <button @click="fontSizeValue++"> + </button>
        <button @click="fontSizeValue--"> - </button>
    </div>
</template>

<script>
import { computed, ref } from 'vue';

export default {
    setup () {
        
        const fontSizeValue = ref(13)
        const styleObject = computed(() => {
            return {
                fontSize: fontSizeValue.value + 'px',
                color: 'chocolate'
            };
        });

        return { styleObject, fontSizeValue }
    }
}
</script>

<style lang="scss" scoped>
    button { width: 200px; height: 100px; }
</style>