<template>
    <section>
        Killers Perks
        <v-list>
            <v-list-item v-for="killersPerk in killersPerks" :key="killersPerk.id">
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
            killersPerks: [],
        }
    },
    methods: {
        async fetchKillersPerks() {
            this.killersPerks = await fetch('/killers-perks.json').then((res) => res.json())
            console.log(this.killersPerks)
        }
    },
    mounted() {
        this.fetchKillersPerks()
    }
})
</script>
