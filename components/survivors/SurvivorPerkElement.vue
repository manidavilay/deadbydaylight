<template>
  <base-perk-card>
    <template v-slot:icon>
       <img
        :src="survivorPerkElementIcon"
        alt="survivor-perk-icon"
      />
    </template>
    <template v-slot:name>
      {{ survivorPerkElementName }}
    </template>
    <template v-slot:rank>
      <p v-html="survivorPerkElementRank" class="mb-1"></p>
    </template>
    <template v-slot:character>
      {{ survivorPerkElementCharacter }}
    </template>
    <template v-slot:description>
      <p v-html="survivorPerkElementDescription"></p>
    </template>
  </base-perk-card>
</template>

<script>
import BasePerkCard from '../UI/BasePerkCard.vue';

export default {
  components: {
    BasePerkCard,
  },
  props: [
    "id",
    "survivorPerkElementIcon",
    "survivorPerkElementName",
    "survivorPerkElementCharacter",
    "survivorPerkElementDescription",
    "survivorPerkElementRank",
  ],
};
</script>