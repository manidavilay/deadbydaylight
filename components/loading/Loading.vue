<template>
  <section class="loading black">
    <img :src="gif" alt="Dead By Daylight loading" class="loading__gif" />
  </section>
</template>

<script>
export default {
  data() {
    return {
      gif: require("../../static/dbd.gif"),
    };
  },
};
</script>

<style lang="scss">
.loading {
  position: fixed;
  z-index: 800;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100vh;
  background-color: black;
  pointer-events: none;
  overflow: hidden;
  transition: opacity 0.7s ease-in-out;

  &.isDoneLoading {
    opacity: 0;
  }

  &__gif {
    width: 50%;

    @media all and (max-width: 900px) {
      width: 100%;
    }
  }
}
</style>
