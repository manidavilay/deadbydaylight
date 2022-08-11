<template>
  <base-character-card>
    <template v-slot:portrait>
      <img :src="killerElementPortrait" alt="killer-portrait" />
    </template>
    <template v-slot:name>
      {{ killerElementName }}
    </template>
    <template v-slot:rank>
      <p v-html="killerElementRank" class="mb-1"></p>
    </template>
    <template v-slot:infos>
      <p class="mb-1">
        <span class="infos">Gender:</span> {{ killerElementGender }} <br />
      </p>
      <p class="mb-1">
        <span class="infos">Power:</span> {{ killerElementPower }} <br />
      </p>
      <p class="mb-1">
        <span class="infos">Weapon:</span> {{ killerElementWeapon }} <br />
      </p>
      <p class="mb-1">
        <span class="infos">Nationality:</span> {{ killerElementNationality }}
        <br />
      </p>
      <p class="mb-1">
        <span class="infos">Difficulty:</span> {{ killerElementDifficulty }}
        <br />
      </p>
    </template>
    <template v-slot:characterPerk>
      <v-row>
        <v-list-item
          v-for="perk in killerElementPerks"
          :key="perk.id"
          class="d-flex flex-column col-12 col-md-4"
        >
          <img v-if="perk.icon" :src="perk.icon" alt="killer-perk-icon" />
          <h3 v-html="perk.name" class="mb-4"></h3>
          <p v-html="perk.description"></p>
        </v-list-item>
      </v-row>
    </template>
  </base-character-card>
</template>

<script>
import BaseCharacterCard from "../UI/BaseCharacterCard.vue";

export default {
  components: {
    BaseCharacterCard,
  },
  props: [
    "id",
    "killerElementPortrait",
    "killerElementName",
    "killerElementGender",
    "killerElementPower",
    "killerElementWeapon",
    "killerElementNationality",
    "killerElementDifficulty",
    "killerElementRank",
    "killerElementPerks",
  ],
};
</script>