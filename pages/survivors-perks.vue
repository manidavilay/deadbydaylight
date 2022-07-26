<template>
    <section>
        Survivors Perks
        <v-text-field
          placeholder="Search for a perk"
          v-model="search"
        ></v-text-field>
        <v-list>
            <v-list-item v-for="survivorsPerk in filteredSurvivorsPerks" :key="survivorsPerk.id">
                <img :src="survivorsPerk.icon" alt="">
                {{ survivorsPerk.name }} <br>
                {{ survivorsPerk.character }} <br>
                {{ survivorsPerk.description }}
            </v-list-item>
        </v-list>
    </section>
</template>

<script>
export default {
    data() {
        return {
            search: '',
            survivorsPerks: []
        }
    },
    methods: {
        async fetchSurvivorPerks() {
            this.survivorsPerks = await fetch('/survivors-perks.json').then((res) => res.json())
            console.log(this.survivorsPerks)
        }
    },
    computed: {
        filteredSurvivorsPerks() {
            return this.survivorsPerks.filter(perk => {
                if (perk.name.toLowerCase().includes(this.search.toLowerCase())) {
                    return perk.name.toLowerCase().includes(this.search.toLowerCase())
                }
            })
        }
    },
    mounted() {
        this.fetchSurvivorPerks();
    }
}
</script>
