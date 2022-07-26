<template>
    <section>
        Killers Perks
        <v-text-field
          placeholder="Search for a killer perk"
          v-model="search"
        ></v-text-field>
        <v-list>
            <v-list-item v-for="killersPerk in filteredKillersPerks" :key="killersPerk.id">
                <img :src="killersPerk.icon" alt="">
                {{ killersPerk.name }} <br>
                {{ killersPerk.character }} <br>
                {{ killersPerk.description }}
            </v-list-item>
        </v-list>
    </section>
</template>

<script>
export default ({
    data() {
        return {
            search: '',
            killersPerks: [],
        }
    },
    methods: {
        async fetchKillersPerks() {
            this.killersPerks = await fetch('/killers-perks.json').then((res) => res.json())
            console.log(this.killersPerks)
        }
    },
    computed: {
        filteredKillersPerks() {
            return this.killersPerks.filter(perk => {
                if (perk.name.toLowerCase().includes(this.search.toLowerCase())) {
                    return perk.name.toLowerCase().includes(this.search.toLowerCase())
                }
            })
        }
    },
    mounted() {
        this.fetchKillersPerks()
    }
})
</script>
