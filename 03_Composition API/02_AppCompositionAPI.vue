<!-- Composition API  -vue3
  옵션을 선언하는 대신에 가져온 함수를 사용하여  Vue컴포넌트를 작성할 수 있는 API세트, 같이 사용 가능함(권장하진 않음)
  -공식 문서 example가보면 왼쪽 버튼에서 비교가능
-->
<template>
  <div>
    <button v-on:click="increment">Counter:  {{ counter }}</button>
  </div>
</template>

<script>
  import { onMounted, ref } from "vue";

  export default {    
    setup() {
      const counter = ref(0);
      const increment = () => counter.value++;
      
      onMounted(() => {
      console.log('컴포넌트 마운트 됨!')
        });

      return {
        counter,
        increment,
      };
    },
  }
</script>

<style lang="scss" scoped>

</style>