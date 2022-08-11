<template>
  <base-perk-card>
    <template v-slot:icon>
       <img
        :src="killerPerkElementIcon"
        alt="killer-perk-icon"
      />
    </template>
    <template v-slot:name>
      {{ killerPerkElementName }}
    </template>
    <template v-slot:rank>
      <p v-html="killerPerkElementRank" class="mb-1"></p>
    </template>
    <template v-slot:character>
      {{ killerPerkElementCharacter }}
    </template>
    <template v-slot:description>
      <p v-html="killerPerkElementDescription"></p>
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
    "killerPerkElementIcon",
    "killerPerkElementName",
    "killerPerkElementCharacter",
    "killerPerkElementDescription",
    "killerPerkElementRank",
  ],
};
</script>