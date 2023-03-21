<template>
  <div class="home">
    <h1> hello,{{ title }}</h1>
    <div v-html="htmlTag"></div>
    <figure><img :src="imgUrl"></figure>
    <div class="menu" :class="{active:isActive}" @click="toggle">토글 메뉴</div>
    <ul>
      <li v-for="(v,k) in data" :key="k">
        <p v-if="v.name == 'react'">{{ v.name }}</p>
      </li>
    </ul>
    <div class="ip">
      <input type="text" v-model="elInput[0]">
      <input type="text" v-model="elInput[1]">
      <button @click="result">확인</button>
    </div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      title : 'JUB world!',
      htmlTag : '<p style="color:red">v-html</p>',
      imgUrl : require('@/assets/logo.png'),
      isActive : true,
      data : [
        {id:11, name:'react'},
        {id:22, name:'vue'}
      ],
      elInput : ['이주은','돼지']
    }
  },
  methods: {
    result(){
      console.log(this.elInput)
    },
    toggle(){
      this.isActive = !this.isActive;
    }
  }
  // updated() {
  //   console.log('재랜더링 발생');
  // },
  // created() {
  //   console.log('init created')
  // },
  // mounted() {
  //   console.log('mounted')
  // },
  // unmounted() {
  //   console.log('unmounted')
  // },
}
</script>

<style lang="scss">
  .menu{
    font-size: 3rem;
    &.active{color: red;}
  }
</style>