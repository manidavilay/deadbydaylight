<template>
  <section class="d-flex align-center py-10 perk">
    <v-row>
      <v-col class="col-12 col-sm-3 d-flex flex-column justify-center align-center mb-4 mb-sm-0 mr-0 mr-sm-4 text-center perk__name">
        <slot name="icon"></slot>
        <h2>
          <slot name="name"></slot>
        </h2>
      </v-col>
      <v-col class="col-12 col-sm-8 d-flex flex-column perk__description">
        <div class="d-flex">
          <span class="mr-1 perk__info">Rank:</span>
          <slot name="rank"></slot>
        </div>
        <p class="mb-1">
          <span class="perk__info">Character:</span>
          <slot name="character"></slot>
        </p>
        <br />
        <slot name="description"></slot>
      </v-col>
    </v-row>
  </section>
</template>

<style lang="scss">
.perk {
    border-top: 1px solid #ffffff;

  &__name {
    width: 30%;

    img {
      width: 150px;
    }
  }

  &__info {
    font-weight: bold;
  }

  &__description {
    width: 70%;
  }
}
</style>