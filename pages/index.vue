<template>
  <section class="mx-auto homepage">
    <v-row>
      <v-col>
        <img :src="image" alt="Dead By Daylight image" class="mb-10 homepage__image" />
        <p v-html="description" class="mb-4"></p>
      </v-col>
    </v-row>
  </section>
</template>

<script>
import Loading from '../components/loading/Loading.vue';

export default {
  name: "IndexPage",
  components: {
    Loading
  },
  data() {
    return {
      image: require('../static/deadbydaylight-image.jpeg'),
      description:
        "Dead by Daylight is a <b>multiplayer (4vs1) horror game</b> where one player takes on the role of the <b>savage Killer</b>, and the other four players play as <b>Survivors</b>, trying to <bescape the Killer</b> and avoid being caught, tortured and killed. Survivors play in third-person and have the advantage of better situational awareness. Survivors need to <b>find generators in the map and fix them</b> in order to <b>open the gate and escape</b> before being found and killed by the Killer."
    };
  },
};
</script>

<style lang="scss">
.homepage {
  width: 85%;

  &__image {
    width: 100%;
  }
}
</style>
