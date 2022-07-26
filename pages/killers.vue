<template>
    <section>
        Killers
        <v-text-field
          placeholder="Search for a killer"
          v-model="search"
        ></v-text-field>
        <v-list>
          <v-list-item v-for="killer in filteredKillers" :key="killer.id" class="my-13">
          <div class="d-flex flex-column align-center text-center">
            <img :src="killer.portrait" alt="">
            <h2>{{ killer.name }} </h2> <br>
            Full name: {{ killer.full_name }} <br>
            Gender :{{ killer.gender }} <br>
            Nationality: {{ killer.nationality }} <br>
            Height: {{ killer.height }} <br>
            Power: {{ killer.power }} <br>
            Weapon: {{ killer.weapon }} <br>
            Realm: {{ killer.realm }} <br>
            Speed: {{ killer.speed }} <br>
            Terror radius: {{ killer.terror_radius }} <br>
            Difficulty: {{ killer.difficulty }} <br>
          </div>
           <v-list-item v-for="perk in killer.perks" :key="perk.id">
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
      killers: [],
    }
  },
  methods: {
    async fetchKillers() {
      this.killers = await fetch('/killers.json').then((res) => res.json())
    },
  },
  computed: {
    filteredKillers() {
      return this.killers.filter(killer => {
        if (killer.name.toLowerCase().includes(this.search.toLowerCase())) {
          return killer.name.toLowerCase().includes(this.search.toLowerCase())
        }
      })
    }
  },
  mounted() {
      this.fetchKillers();
  }
}
</script>
