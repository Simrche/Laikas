<template>
    <button class="tools" v-on:click="chronoTime()">
        <img src="../assets/chronometres.png" alt="Chronometre">
        <p>Chronomètre</p>
    </button>
    <button class="tools" v-on:click="minuteTime()">
        <img src="../assets/minuteur.png" alt="Minuteur">
        <p>Minuteur (SOON)</p>
    </button>
</template>

<script>
export default {
    name: 'Sidebar',
    methods: {
        chronoTime() {
            this.$emit('chrono')
        },

        minuteTime() {
            this.$emit('minu')
        },
    }
}
</script>

<style scoped>
    .tools {
        width: 200px;
        height: 200px;
        margin-top: 50px;
        font-family: Poppins;
        font-size: 20px;
    }

    .tools img {
        width: 125px;
        height: 125px;
    }
</style>