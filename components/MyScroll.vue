<template>
  <section class="container">
    <div>
      <!-- v-scroll="handleScroll" で可視範囲に入った時に発火-->
      <div class="box" v-scroll="handleScroll">scroll hock</div>
    </div>
  </section>
</template>

<script>
export default {
  methods: {
    handleScroll: function(evt, el) {
      console.log(window.scrollY);
      if (window.scrollY > 50) {
        el.setAttribute(
          // 可視範囲に入った時に追加されるcssを記述
          "style",
          "opacity: 1; transform: translate3d(0, -10px, 0)"
        );
      }
      return window.scrollY > 100;
    }
  }
};
</script>

<style scoped>
.container {
  min-height: 150vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
  
/*最初はboxというclassがついた要素は非表示*/
.box {
  opacity: 0;
  transition: 1.5s all cubic-bezier(0.39, 0.575, 0.565, 1);
}
</style>