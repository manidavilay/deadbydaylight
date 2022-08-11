<template>
  <section>
    <base-search>
      <v-text-field
        placeholder="Search for a killers"
        v-model="search"
      ></v-text-field>
    </base-search>
    <p v-if="notFound" class="text-center">
      {{ killerNotFound }}
    </p>
    <v-list class="black">
      <killer-element
        v-for="killer in filteredKillers"
        :id="killer.id"
        :key="killer.id"
        :killerElementPortrait="killer.portrait"
        :killerElementName="killer.name"
        :killerElementGender="killer.gender"
        :killerElementPower="killer.power"
        :killerElementWeapon="killer.weapon"
        :killerElementNationality="killer.nationality"
        :killerElementDifficulty="killer.difficulty"
        :killerElementRank="killer.rank"
        :killerElementPerks="killer.perks"
      ></killer-element>
    </v-list>
  </section>
</template>

<script>
import BaseSearch from '../UI/BaseSearch.vue';
import KillerElement from "./KillerElement.vue";

export default {
  components: {
    BaseSearch,
    KillerElement,
  },
  props: ["killers"],
  data() {
    return {
      search: "",
      notFound: false,
      killerNotFound: "Sorry, the killer you're looking for can't be found, please try again."
    };
  },
  computed: {
    filteredKillers() {
      const filteredKillers = this.killers.filter((killer) => {
        if (killer.name.toLowerCase().includes(this.search.toLowerCase())) {
          return killer.name
            .toLowerCase()
            .includes(this.search.toLowerCase());
        }
      });
      if (filteredKillers == 0) {
        this.notFound = true
      } else {
        this.notFound = false
        return filteredKillers;
      }
    },
  },
};
</script>