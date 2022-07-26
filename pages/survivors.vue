<template>
  <section>
    Survivors
    <v-text-field
      placeholder="Search for a survivor"
      v-model="search"
    ></v-text-field>
    <div v-if="$fetchState.pending">
      <p>Content is loading...</p>
    </div>
    <v-list class="d-flex flex-column survivors" v-else>
      <v-list-item
        v-for="survivor in filteredSurvivors"
        :key="survivor.id"
        class="my-13"
      >
        <div class="d-flex flex-column align-center text-center">
          <img :src="survivor.portrait" alt="" />
          <h2 class="survivors-name">{{ survivor.name }}</h2>
          <br />
          Gender: {{ survivor.gender }} <br />
          Role: {{ survivor.role }} <br />
          Nationality: {{ survivor.nationality }} <br />
          Difficulty: {{ survivor.difficulty }} <br />
        </div>
        <v-list-item v-for="perk in survivor.perks" :key="perk.id" class="perk">
          {{ perk }}
        </v-list-item>
      </v-list-item>
    </v-list>
  </section>
</template>

<script>
export default {
  data() {
    return {
      search: "",
      survivors: [],
    };
  },
  async fetch() {
    const res = await this.$axios.get('/survivors.json')
    this.survivors = res.data
  },
  fetchOnServer: false,
  computed: {
    filteredSurvivors() {
      return this.survivors.filter((survivor) => {
        if (survivor.name.toLowerCase().includes(this.search.toLowerCase())) {
          return survivor.name
            .toLowerCase()
            .includes(this.search.toLowerCase());
        }
      });
    },
  },
};
</script>