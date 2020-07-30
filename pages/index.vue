<template>
  <div class="container">
    <my-menu />
    <my-swiper />
    <my-scroll />
    
    <div class="example-modal-window">
    <p>ボタンを押すとモーダルウィンドウが開きます</p>
    <button @click="openModal">開く</button>

    <!-- コンポーネント MyModal -->
    <MyModal @close="closeModal" v-if="modal">
      <!-- default スロットコンテンツ -->
      <p>ここがモーダル内のテキスト</p>
      <div><input v-model="message"></div>
      <!-- /default -->
      <!-- footer スロットコンテンツ -->
      <template slot="footer">
        <button @click="doSend">送信</button>
      </template>
      <!-- /footer -->
    </MyModal>
  </div>
  </div>
</template>

<script>
import MyMenu from '~/components/MyMenu.vue'
import MyScroll from '~/components/MyScroll.vue'
import MySwiper from '~/components/MySwiper.vue'
import MyModal from '~/components/MyModal.vue'

export default {
  components: {
    MyMenu,
    MyScroll,
    MySwiper,
    MyModal
  },
    data() {
    return {
      modal: false,
      message: ''
    }
  },
  methods: {
    openModal() {
      this.modal = true
    },
    closeModal() {
      this.modal = false
    },
    doSend() {
      if (this.message.length > 0) {
        alert(this.message)
        this.message = ''
        this.closeModal()
      } else {
        alert('メッセージを入力してください')
      }
    }
  }
}
</script>

<style lang="scss">
  .container {
    text-align: center;
    padding-bottom: 5em;
  }
</style>