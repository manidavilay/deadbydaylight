<template>
  <base-list>
    <template v-slot:title>
      Killers Perks
    </template>
    <template v-slot:content>
      <killer-perk-list :killersPerks="killersPerks"></killer-perk-list>
    </template>
  </base-list>
</template>

<script>
import BaseList from '../components/UI/BaseList.vue';
import KillerPerkList from '../components/killers/KillerPerkList.vue';
import killersPerks from '../static/killersPerks.json';

export default {
  components: {
    BaseList,
    KillerPerkList
  },
  data() {
    return {
      killersPerks
    };
  },
};
</script>