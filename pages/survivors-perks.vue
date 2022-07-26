<template>
    <section>
        Survivors Perks
        <v-list>
            <v-list-item v-for="survivorsPerk in survivorsPerks" :key="survivorsPerk.id">
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
            survivorsPerks: []
        }
    },
    methods: {
        async fetchSurvivorPerks() {
            this.survivorsPerks = await fetch('/survivors-perks.json').then((res) => res.json())
            console.log(this.survivorsPerks)
        }
    },
    mounted() {
        this.fetchSurvivorPerks();
    }
}
</script>
