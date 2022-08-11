<template>
  <section class="survivors-list">
    <base-search>
      <v-text-field
        placeholder="Search for a survivor"
        v-model="search"
      ></v-text-field>
    </base-search>
    <p v-if="notFound" class="text-center">
      {{ survivorNotFound }}
    </p>
    <v-list class="black">
      <survivor-element
        v-for="survivor in filteredSurvivors"
        :id="survivor.id"
        :key="survivor.id"
        :survivorElementPortrait="survivor.portrait"
        :survivorElementName="survivor.name"
        :survivorElementGender="survivor.gender"
        :survivorElementRole="survivor.role"
        :survivorElementNationality="survivor.nationality"
        :survivorElementDifficulty="survivor.difficulty"
        :survivorElementRank="survivor.rank"
        :survivorElementPerks="survivor.perks"
      ></survivor-element>
    </v-list>
  </section>
</template>

<script>
import BaseSearch from '../UI/BaseSearch.vue';
import SurvivorElement from "./SurvivorElement.vue";

export default {
  components: {
    BaseSearch,
    SurvivorElement,
  },
  props: ["survivors"],
  data() {
    return {
      search: "",
      notFound: false,
      survivorNotFound: "Sorry, the survivor you're looking for can't be found, please try again"
    };
  },
  computed: {
    filteredSurvivors() {
      const filteredSurvivors = this.survivors.filter((survivor) => {
        if (survivor.name.toLowerCase().includes(this.search.toLowerCase())) {
          return survivor.name
            .toLowerCase()
            .includes(this.search.toLowerCase());
        }
      });
      if (filteredSurvivors == 0) {
        this.notFound = true
      } else {
        this.notFound = false
        return filteredSurvivors;
      }
    },
  },
};
</script>