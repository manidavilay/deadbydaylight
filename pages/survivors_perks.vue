<template>
  <base-list>
    <template v-slot:title>
      Survivors Perks
    </template>
    <template v-slot:content>
      <survivor-perk-list :survivorsPerks="survivorsPerks"></survivor-perk-list>
    </template>
  </base-list>
</template>

<script>
import BaseList from '../components/UI/BaseList.vue';
import SurvivorPerkList from '../components/survivors/SurvivorPerkList.vue';
import survivorsPerks from '../static/survivorsPerks.json';

export default {
  components: {
    BaseList,
    SurvivorPerkList
  },
  data() {
    return {
      survivorsPerks
    };
  },
};
</script>