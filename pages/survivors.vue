<template>
  <section>
    Survivors
    <v-text-field
      placeholder="Search for a survivor"
      v-model="search"
    ></v-text-field>
    <v-list class="d-flex flex-column survivors">
      <v-list-item v-for="survivor in filteredSurvivors" :key="survivor.id" class="my-13">
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
      search: '',
      survivors: [],
    };
  },
  methods: {
    async fetchSurvivors() {
      this.survivors = await fetch("/survivors.json").then(res => res.json())
    },
  },
  computed: {
    filteredSurvivors() {
      return this.survivors.filter(survivor => {
        if (survivor.name.toLowerCase().includes(this.search.toLowerCase())) {
          return survivor.name.toLowerCase().includes(this.search.toLowerCase())
        }
      })
    },
  },
  mounted() {
    this.fetchSurvivors()
  },
};
</script>