<template>
  <base-character-card>
    <template v-slot:portrait>
      <img :src="survivorElementPortrait" alt="survivor-portrait" />
    </template>
    <template v-slot:name>
      {{ survivorElementName }}
    </template>
    <template v-slot:rank>
      <p v-html="survivorElementRank" class="mb-1"></p>
    </template>
    <template v-slot:infos>
      <p class="mb-1">
        <span class="infos">Gender:</span> {{ survivorElementGender }} <br />
      </p>
      <p class="mb-1">
        <span class="infos">Role:</span> {{ survivorElementRole }} <br />
      </p>
      <p class="mb-1">
        <span class="infos">Nationality:</span> {{ survivorElementNationality }} <br />
      </p>
      <p class="mb-1">
        <span class="infos">Difficulty:</span> {{ survivorElementDifficulty }} <br />
      </p>
    </template>
    <template v-slot:characterPerk>
      <v-row>
        <v-list-item
          v-for="perk in survivorElementPerks"
          :key="perk.id"
          class="d-flex flex-column col-12 col-md-4"
        >
          <img v-if="perk.icon" :src="perk.icon" alt="survivor-perk-icon" />
          <h3 v-html="perk.name" class="mb-4"></h3>
          <p v-html="perk.description"></p>
        </v-list-item>
      </v-row>
    </template>
  </base-character-card>
</template>

<script>
import BaseCharacterCard from '../UI/BaseCharacterCard.vue';

export default {
  components: {
    BaseCharacterCard
  },
  props: [
    "id",
    "survivorElementPortrait",
    "survivorElementName",
    "survivorElementGender",
    "survivorElementRole",
    "survivorElementNationality",
    "survivorElementDifficulty",
    "survivorElementPerks",
    "survivorElementRank"
  ],
};
</script>