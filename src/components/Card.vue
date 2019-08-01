<template>
  <div id="card">
    <div class="cp-border">
      <div  class="cp-div-img" @mouseover="openMessage" ref="el">
        <img :src="service.img" alt="">
      </div>
    </div>
  
    <transition name="slide">
      <div v-if="showMessage" class="cp-message">
        <h2>{{ service.description }}</h2>
      </div>
    </transition>
  
  </div>
</template>

<script>
  export default {
    name: "Card",
    props: ['service'],
    data() {
      return {
        showMessage: false,
        canClose: false
      }
    },
    methods: {
      openMessage() {
        if(this.showMessage)
          return
        this.$refs.el.classList.add('cp-selected')
        this.showMessage = true
        setTimeout(() => {
          this.showMessage = false
          this.$refs.el.classList.remove('cp-selected')
        }, 8000)
      }
    }
    
  }
</script>

<style scoped>
  
  .cp-message {
    /*background: #2a00ff;*/
    background: rgb(4, 0, 65);
    background: linear-gradient(90deg, rgb(102, 118, 238) 0%, rgba(5, 5, 242, 0.8953956582633054) 69%, rgba(0, 212, 255, 1) 100%);
    position: absolute;
    height: 300px;
    opacity: 0.9;
    z-index: 100;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-family: 'Indie Flower', cursive;
    font-weight: 900;
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 10px;
    padding-left: 30px;
    padding-right: 30px;
  }
  
  .cp-message h2 {
    text-align: center;
    font-weight: 900;
  }
  
  .cp-div-img {
    margin: 20px 0;
  }
  
  .cp-div-img > img {
    width: 180px;
    height: 90px;
    border-radius: 40px 50px 40px 50px;
  }
  
  .cp-selected {
    transform: rotate(10deg);
  }

  .slide-enter, .slide-leave-to {
    /*position: fixed;*/
    left: -150%;
    transition: 1s ease-out;
    opacity: 0;
  }

  .slide-enter-to, .slide-leave {
    left: 50%;
    transition: 1s ease-out;
    opacity: 0.9;
  }

  @media (max-width: 950px) {
    .cp-message{
      height: 90%;
      position: fixed;
    }
  }

</style>