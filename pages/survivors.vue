<template>
    <section>
        Survivors
        <v-list>
          <v-list-item v-for="survivor in survivors" :key="survivor.id">
           {{ survivor.name }} <br>
           <img :src="survivor.portrait" alt="">
           {{ survivor.gender }} <br>
           {{ survivor.role }} <br>
           {{ survivor.nationality }} <br>
           {{ survivor.difficulty }} <br>
           <v-list-item v-for="perk in survivor.perks" :key="perk.id">
            <li>{{ perk }}</li>
           </v-list-item>
          </v-list-item>
        </v-list>
    </section>
</template>

<script>
export default {
  data() {
    return {
      survivors: [],
    }
  },
  methods: {
    async fetchSurvivors() {
      this.survivors = await fetch('/survivors.json').then((res) => res.json())
      console.log(this.survivors)
    },
  },
  mounted() {
    this.fetchSurvivors();
  }
}
</script>
