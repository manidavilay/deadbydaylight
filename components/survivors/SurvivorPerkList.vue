<template>
    <section>
      <base-search>
        <v-text-field
        placeholder="Search for a survivor perk"
        v-model="search"
        ></v-text-field>
      </base-search>
        <p v-if="notFound" class="text-center">
          {{ perkNotFound }}
        </p>
        <survivor-perk-element
        v-for="survivorPerk in filteredSurvivorsPerks"
        :id="survivorPerk.id"
        :key="survivorPerk.id"
        :survivorPerkElementIcon="survivorPerk.icon"
        :survivorPerkElementName="survivorPerk.name"
        :survivorPerkElementCharacter="survivorPerk.character"
        :survivorPerkElementDescription="survivorPerk.description"
        :survivorPerkElementRank="survivorPerk.rank"
        ></survivor-perk-element>
    </section>
</template>

<script>
import BaseSearch from '../UI/BaseSearch.vue';
import SurvivorPerkElement from "./SurvivorPerkElement.vue";

export default {
  components: {
    BaseSearch,
    SurvivorPerkElement,
  },
  props: ["survivorsPerks"],
  data() {
      return {
          search: "",
          notFound: false,
          perkNotFound: "Sorry, the perk you're looking for can't be found, please try again"
      }
  },
  computed: {
    filteredSurvivorsPerks() {
      const filteredSurvivorsPerks = this.survivorsPerks.filter((perk) => {
        if (perk.name.toLowerCase().includes(this.search.toLowerCase())) {
          return perk.name.toLowerCase().includes(this.search.toLowerCase());
        }
      });
      if (filteredSurvivorsPerks == 0) {
        this.notFound = true
      } else {
        this.notFound = false
        return filteredSurvivorsPerks;
      }
    },
  },
};
</script>