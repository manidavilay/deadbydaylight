<template>
  <section>
    Killers Perks
    <v-text-field
      placeholder="Search for a perk"
      v-model="search"
    ></v-text-field>
    <div v-if="$fetchState.pending">
      <p>Content is loading...</p>
    </div>
    <v-list v-else>
      <v-list-item
        v-for="killersPerk in filteredKillersPerks"
        :key="killersPerk.id"
      >
        <div class="d-flex flex-column align-items text-center">
          <img :src="killersPerk.icon" alt="" />
          <h2>{{ killersPerk.name }}</h2>
          <br />
        </div>
        Character: {{ killersPerk.character }} <br />
        Description: {{ killersPerk.description }}
      </v-list-item>
    </v-list>
  </section>
</template>

<script>
export default {
  data() {
    return {
      search: "",
      killersPerks: [],
    };
  },
  async fetch() {
    const res = await this.$axios.get('/killers-perks.json')
    this.killersPerks = res.data
  },
  fetchOnServer: false,
  computed: {
    filteredKillersPerks() {
      return this.killersPerks.filter((perk) => {
        if (perk.name.toLowerCase().includes(this.search.toLowerCase())) {
          return perk.name.toLowerCase().includes(this.search.toLowerCase());
        }
      });
    },
  },
};
</script>
