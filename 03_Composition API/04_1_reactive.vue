<template>
  <div>
    <h2>reactive()</h2>
    -객체 타입에만 동작,  depth가 깊어졌을때도 그대로 영향을 줌
    <button v-on:click="increment">Click: {{ state.count }}</button>
    <button v-on:click="increment">Click: {{ state.deep.count2 }}</button>
  </div>
</template>

<script>
import { reactive} from 'vue';

export default {
  setup () {
    let state = reactive({
      count: 0,
      deep:{ count2: 0 }  
    });
    const increment = ()=>{
      state.count++;    //ref()에서는 .value가 붙음
      state.deep.count2++
    }

    return {
      state,
      increment
    }
  }
}
</script>

<style scoped>

</style>