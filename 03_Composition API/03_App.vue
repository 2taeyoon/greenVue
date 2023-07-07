<!-- Composition API
  옵션을 선언하는 대신에 가져온 함수를 사영하여 컴포넌트를 작성
-->
<template>
  <div class="box">
    <h2>setup hook</h2>
    setup() 함수(hook)는 Composition API  사용을 위한 진입전 역할<br>
    컴포넌트 인스턴스가 생성되기 전에 실행
  </div>
  <div class="box box2">
    <h2>Reactivity: 반응성</h2>
    <p>Reactivity메세지 : <span>{{ reactiveMessage }} </span><br>
      <button v-on:click="addReactiveMsg">Add Message</button>
    </p>
    <p>Normal메세지 : <span>{{ noramlMessage }} </span><br>
      <button v-on:click="addNoramlMsg">Add Message</button>
    </p>
  </div>
  <div class="box">
    <h2>Lifecycle Hooks</h2>
    Vue 인스턴스나 컴포넌트가 생성되고, 작동하고, 삭제될때 단계를 거치게 되는데 이를 라이프 사이클이라고 한다<br>
    create → mount → update → destroy 
    <p> {{ aaa }} </p>
    <p> {{ bbb }} </p>
  </div>
</template>

<script>
import { ref,isRef,onMounted,onBeforeMount } from 'vue';

export default {
  setup () {
    const reactiveMessage = ref('리액티브 메세지');
    const addReactiveMsg =()=>{
      reactiveMessage.value = reactiveMessage.value + '!';
    }
    //console.log('reactiveMessage? ', isRef(reactiveMessage));


    let noramlMessage = '노말한 메세지';
    const addNoramlMsg =()=>{
      noramlMessage = noramlMessage + '!';
    }
    //console.log('noramlMessage? ',isRef(addNoramlMsg));

    onMounted(()=>{
      console.log('onMounted')
    });
    onBeforeMount(()=>{
      console.log('onBeforeMount')
    })


    return {
      reactiveMessage,
      noramlMessage,
      addReactiveMsg,
      addNoramlMsg
    }
  }
}
</script>

<style>
  .box { border:1px solid lightgrey; margin:50px 10px; padding:0 20px 20px;}
  .box2 span { color:red}
</style>