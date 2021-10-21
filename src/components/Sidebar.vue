<template>
    <h2>Laikas</h2>
    <button class="tools" v-on:click="chronoTime()" style="margin-top: 50px">
        <img src="../assets/chronometres.png" alt="Chronometre">
        <p>Chronomètre</p>
    </button>
    <button class="tools" v-on:click="minuteTime()">
        <img src="../assets/minuteur.png" alt="Minuteur">
        <p>Minuteur</p>
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

    h2 {
        font-family: "poppins";
    }

    .tools {
        width: 100%;
        font-family: "Poppins";
        font-size: 12px;
        background-color: transparent;
        border: none;
        cursor: pointer;
        padding: 15px 0;
    }

    .tools:hover {
        background-color: rgb(161, 161, 161);
        transition: 0.3s;
    }

    .tools img {
        width: 50px;
        height: 50px;
        
    }
</style>