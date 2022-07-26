<template>
  <section>
    Survivors Perks
    <v-text-field
      placeholder="Search for a perk"
      v-model="search"
    ></v-text-field>
    <div v-if="$fetchState.pending">
      <p>Content is loading...</p>
    </div>
    <v-list v-else>
      <v-list-item
        v-for="survivorsPerk in filteredSurvivorsPerks"
        :key="survivorsPerk.id"
      >
        <div class="d-flex flex-column align-center text-center">
          <img :src="survivorsPerk.icon" alt="" />
          <h2>{{ survivorsPerk.name }}</h2>
          <br />
        </div>
        Character: {{ survivorsPerk.character }} <br />
        Description: {{ survivorsPerk.description }}
      </v-list-item>
    </v-list>
  </section>
</template>

<script>
export default {
  data() {
    return {
      search: "",
      survivorsPerks: [],
    };
  },
  async fetch() {
    const res = await this.$axios.get('/survivors-perks.json')
    this.survivorsPerks = res.data
  },
  fetchOnServer: false,
  computed: {
    filteredSurvivorsPerks() {
      return this.survivorsPerks.filter((perk) => {
        if (perk.name.toLowerCase().includes(this.search.toLowerCase())) {
          return perk.name.toLowerCase().includes(this.search.toLowerCase());
        }
      });
    },
  },
};
</script>
