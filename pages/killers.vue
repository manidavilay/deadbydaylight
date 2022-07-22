<template>
    <section>
        Killers
        <v-list>
          <v-list-item v-for="killer in killers" :key="killer.id">
           {{ killer.name }} <br>
           {{ killer.full_name }} <br>
           <img :src="killer.portrait" alt="">
           {{ killer.gender }} <br>
           {{ killer.nationality }} <br>
           {{ killer.height }} <br>
           {{ killer.power }} <br>
           {{ killer.weapon }} <br>
           {{ killer.realm }} <br>
           {{ killer.speed }} <br>
           {{ killer.terror_radius }} <br>
           {{ killer.difficulty }} <br>
           <v-list-item v-for="perk in killer.perks" :key="perk.id">
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
      killers: [],
    }
  },
  methods: {
    async fetchKillers() {
      this.killers = await fetch('/killers.json').then((res) => res.json())
      console.log(this.killers)
    },
  },
  mounted() {
      this.fetchKillers();
  }
}
</script>
