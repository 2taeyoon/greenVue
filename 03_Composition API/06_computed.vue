<template>
  <div>
    <h2>computed - 계산된 속성</h2>
      - 템플릿 문법이 문법이 길어지면 가독성떨어지고, 유지보수가 어려워지는 것을 방지<br>
      - 계산한 것을 캐싱해주고, 그것을 호출함, 데이타가 변경될때 다시 계산
    <div class="box">
      <h2> {{ lunch.name }}</h2>
      <p>점심메뉴가 나왔나여??</p>
      <!-- <p>{{ lunch.munu.length > 0 ? '네 준비되었습니다! 😊' : '아직 준비중이에요 😭' }}</p>  -->
      <p>computed- {{ hasMenu }}</p>
      <p>computed- {{ hasMenu }}</p>
      <p>일반함수- {{ existMenu() }}</p>
      <p>일반함수- {{ existMenu() }}</p>
      <button v-on:click="counter++">{{ counter }}</button>
      <hr>

      <p>{{ fullName }}</p>

    </div>
  </div>
</template>

<script>
import { computed, ref } from 'vue';

export default {
  setup () {
    const lunch = {
      name:'점심 식단',
      munu:[
        '볶음밥',
        '샐러드',
        '마라탕'
      ]
    }

    const hasMenu = computed(()=> {
      //console.log('computed')
      return lunch.munu.length > 0 ? '네 준비되었습니다! 😊' : '아직 준비중이에요 😭'});
    
    function existMenu(){
      //console.log('일반함수')
      return lunch.munu.length > 0 ? '네 준비되었습니다! 😊' : '아직 준비중이에요 😭'
    }
    const counter = ref(0);

    const firstName = ref('홍');
    const lastName = ref('길동');
    // const fullName = computed(()=> firstName.value +' '+ lastName.value)
    const fullName = computed({
      get(){
        return firstName.value +' '+ lastName.value
      },
      set(value){
        console.log('value ', value);
        [firstName.value, lastName.value] = value.split(' ');

      }
    })

    console.log('수정 전-',fullName.value);
    fullName.value = '전 지현';
    console.log('수정 후-',fullName.value); //readonly 경고뜸

    return {
      lunch,
      hasMenu,
      existMenu,
      counter,
      fullName
    }
  }
}
</script>

<style >
  .box { border:1px solid lightgrey; margin:50px 10px; padding:0 20px 20px;}
  p { margin:3px}
</style>