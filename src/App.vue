<template>
  <div id="app">
    <app-header/>
    <transition name="fade" mode="out-in">
      <router-view></router-view>
    </transition>
    <canvas v-show="showCanvas" id="canvas" key="canvas"></canvas>
    <app-footer/>
  </div>
</template>

<script>
import Header from "./components/Header";
import Footer from "./components/Footer";
export default {
  data() {
    return {
      showCanvas: false
    };
  },
  components: {
    appHeader: Header,
    appFooter: Footer
  },
  watch: {
    $route(to, from) {
      if (this.$router.currentRoute.name === "celebrate") {
        return (this.showCanvas = true);
      } else {
        return (this.showCanvas = false);
      }
      this.$forceUpdate();
    }
  }
};
</script>

<style lang="scss">
.fade-enter {
  opacity: 0;
}
.fade-enter-active {
  transition: opacity 0.3s ease-out;
}
.fade-leave-active {
  transition: opacity 0.3s ease-out;
  opacity: 0;
}
</style>
