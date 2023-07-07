<!--  Options API  
  옵션: 상태, 렌더링,생명주기 .. 구분해서 사용 
-->

<template>
  <div>
    <button v-on:click="increment">Counter: {{ counter }}</button>
  </div>
</template>

<script>
  export default {
    data(){
      return{
        counter:100,
      }
    },
    methods:{
      increment(){
        this.counter++
      }
    },
    mounted(){
      console.log('컴포넌트가 마운트 됨!')
    }
  }
</script>

<style lang="scss" scoped>

</style>