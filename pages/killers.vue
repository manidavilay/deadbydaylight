<template>
  <base-list>
    <template v-slot:title>
      Killers
    </template>
    <template v-slot:content>
      <killer-list :killers="killers"></killer-list>
    </template>
  </base-list>
</template>

<script>
import BaseList from '../components/UI/BaseList.vue';
import KillerList from '../components/killers/KillerList.vue';
import killers from '../static/killers.json'

export default {
  components: {
    BaseList,
    KillerList,
  },
  data() {
    return {
      killers
    };
  },
};
</script>