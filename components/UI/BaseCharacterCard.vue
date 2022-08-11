<template>
    <section class="d-flex flex-column align-center py-10 character">
        <div class="d-flex flex-column align-center mb-10 text-center">
            <slot name="portrait"></slot>
            <h2 class="mt-6">
                <slot name="name"></slot>
            </h2>
            <br />
            <div class="d-flex">
                <span class="mr-1 character__info">Rank:</span>
                <slot name="rank"></slot>
            </div>
            <div class="character__infos">
                <slot name="infos"></slot>
            </div>
        </div>
        <div class="d-flex character__perk">
            <slot name="characterPerk" class="d-flex flex-column"></slot>
            </div>
    </section>
</template>

<style lang="scss">
.character {
  border-top: 1px solid #FFFFFF;

  &__portrait {
    width: 180px;
  }

    &__perk {
        img {
            width: 100px;
        }
    }
    
    &__infos {
        .infos {
            font-weight: bold;
        }
    }
}
</style>