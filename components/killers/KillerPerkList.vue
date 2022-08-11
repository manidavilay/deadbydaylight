<template>
    <section>
      <base-search>
        <v-text-field
        placeholder="Search for a killer perk"
        v-model="search"
        ></v-text-field>
      </base-search>
        <p v-if="notFound" class="text-center">
          {{ perkNotFound }}
        </p>
        <killer-perk-element
        v-for="killerPerk in filteredKillersPerks"
        :id="killerPerk.id"
        :key="killerPerk.id"
        :killerPerkElementIcon="killerPerk.icon"
        :killerPerkElementName="killerPerk.name"
        :killerPerkElementCharacter="killerPerk.character"
        :killerPerkElementDescription="killerPerk.description"
        :killerPerkElementRank="killerPerk.rank"
        ></killer-perk-element>
    </section>
</template>

<script>
import BaseSearch from '../UI/BaseSearch.vue';
import KillerPerkElement from "./KillerPerkElement.vue";

export default {
  components: {
    BaseSearch,
    KillerPerkElement,
  },
  props: ["killersPerks"],
  data() {
      return {
          search: "",
          notFound: false,
          perkNotFound: "Sorry, the perk you're looking for can't be found, please try again"
      }
  },
  computed: {
    filteredKillersPerks() {
      const filteredKillersPerks = this.killersPerks.filter((perk) => {
        if (perk.name.toLowerCase().includes(this.search.toLowerCase())) {
          return perk.name.toLowerCase().includes(this.search.toLowerCase());
        }
      });
      if (filteredKillersPerks == 0) {
        this.notFound = true
      } else {
        this.notFound = false
        return filteredKillersPerks;
      }
    },
  },
};
</script>