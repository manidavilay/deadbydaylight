<template>
  <base-list>
    <template v-slot:title>
      Survivors
    </template>
    <template v-slot:content>
      <survivor-list :survivors="survivors"></survivor-list>
    </template>
  </base-list>
</template>

<script>
import BaseList from '../components/UI/BaseList.vue';
import SurvivorList from '../components/survivors/SurvivorList.vue';
import survivors from '../static/survivors.json'

export default {
  components: {
    BaseList,
    SurvivorList,
  },
  data() {
    return {
      survivors
    };
  },
};
</script>