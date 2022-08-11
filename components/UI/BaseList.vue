<template>
    <section class="mx-auto list">
        <h1 class="mx-auto mb-10 text-center list__title">
            <slot name="title"></slot>
        </h1>
        <slot name="content"></slot>
    </section>
</template>

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
}
</style>