<template>
    <section class="mx-auto list">
        <h1 class="mx-auto mb-10 text-center list__title">
            <slot name="title"></slot>
        </h1>
        <slot name="content"></slot>
        <v-btn fixed icon class="list__scroll-up" @click="scrollToTop()">
          <v-icon size="30px" class="pa-2">
            {{ scrollUp }}
          </v-icon>
        </v-btn>
    </section>
</template>

<script>
export default {
  data() {
    return {
      scrollUp: "mdi-arrow-up",
    }
  },
  methods: {
    scrollToTop() {
      window.scrollTo(0,0)
    }
  }
}
</script>

<style lang="scss">
.list {
  width: 85%;

  @media all and (max-width: 600px) {
    width: 100%;
  }

  &__title {
    font-size: 40px;

    @media all and (max-width: 600px) {
      font-size: 30px;
    }
  }

  &__scroll-up {
    bottom: 50px;
    right: 130px;
    border: 1px solid #FFFFFF;

    @media all and (max-width: 960px) {
      right: 70px;
    }

    @media all and (max-width: 600px) {
      right: 15px;
    }
  }
}
</style>