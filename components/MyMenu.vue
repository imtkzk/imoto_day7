<template>
 <div id="app">
  <header class="header">
    <div class="header__menu">
      <div class="header__menu__line" @click="naviOpen" :class="{'is-active': active}">
        <span></span>
        <span></span>
        <span></span>
      </div>
    </div>
  </header>
   <transition name="navi">
  <nav class="navi" v-show="navi">
    <ul class="navi__wrap">
      <li><a href="#">AAA</a></li>
      <li><a href="#">BBB</a></li>
      <li><a href="#">CCC</a></li>
      <li><a href="#">DDD</a></li>
      <li><a href="#">EEE</a></li>
    </ul>
  </nav>
 </transition>
 </div>
</template>

<script>
export default {
  new: '#app',
  data: function() {
        return {
    active: false,
    navi: false,
  }
  },
  methods: {
    naviOpen: function() {
      this.active = !this.active;
      this.navi = !this.navi;
    }
  }
}
</script>

<style lang="scss" scoped>
.header {
  width: 100%;
  background: #fff;
  height: 60px;
  &__menu {
    width: 60px;
    height: 60px;
    position: fixed;
    top: 0;
    right: 0;
    &__line {
      width: 36px;
      height: 30px;
      margin-top: 15px;
      margin-left: auto;
      margin-right: auto;
      position: relative;
      cursor: pointer;
      span {
        width: 100%;
        height: 2px;
        background: #000;
        display: block;
        transition: .6s;
        position: absolute;
        &:first-child {
          top: 0;
        }
        &:nth-child(2) {
          top: 14px;
        }
        &:last-child {
          bottom: 0;
        }
      /* is-activeのクラスがついた時の処理 */   
      }
      &.is-active {
        span {
          transition: .6s;
          &:first-child {
            transform: rotate(45deg);
            top: 50%;
          }
          &:nth-child(2) {
            opacity: 0;
          }
          &:last-child {
            transform: rotate(-45deg);
            top: 50%;
          }
        }
      }
    }
  }
}

 /* メニュー内のスタイル */  
.navi {
  width: 100%;
  position: fixed;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #fff;
  &__wrap {
    list-style-type: none;
    text-align: center;
    padding-left: 0;
    background: #4b4b4b;
    padding: 60px 0;
    width: 100%;
    li {
      a {
        text-decoration: none;
        color: #fff;
        display: block;
        padding: 10px 100px;
      }
    }
  }
  &-enter, &-leave-to {
    opacity: 0;
  }
  &-enter-to, &-leave {
    opacity: 1;
  }
  &-enter-active, &-leave-active {
    transition: .6s;
  }
}
</style>