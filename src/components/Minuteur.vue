<template>
    <h1 v-on="test()">Minuteur</h1>

    <div id="time" v-if="choice">
        <p>{{hour}}</p><p>:</p><p>{{minute}}</p><p>:</p><p>{{seconde}}</p>
    </div>
    <div id="choice" v-if="!choice">
        <div class="choiceIn">
            <label for="minute">Minute :</label>
            <select name="minute" id="" v-model="minute">
                <option v-for="number in numbers" :key="number" v-bind:value="number">{{number}}</option>
            </select>
        </div>
        <div class="choiceIn">
            <label for="seconde" >Seconde :</label>
            <select name="seconde" id="" v-model="seconde">
                <option v-for="number in numbers" :key="number" v-bind:value="number">{{number}}</option>
            </select>
        </div>
        <button v-on:click="go">GO</button>
    </div>
</template>

<script>
export default {
    name: 'Minuteur',
    data() {
      return {
        seconde: 404,
        minute: 404,
        hour: 0,
        choice: false,
        numbers: [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,58,59]
      }
    },
    methods: {
        go() {
            if(this.seconde != 404 && this.minute != 404) {
                this.choice = true

            }
        }
    }
}
</script>

<style scoped>
    h1{
        font-size: 60px;
    }

    p {
        font-size: 100px;
        font-family: 'Orbitron', sans-serif;
        min-width: 20%;
    }

    #time {
        display: flex;
        justify-content: space-around;
        width: 80%;
        margin: 0 auto;
    }

    #choice {
        display: flex;
        justify-content: center;
    }

    #choice button {
        width: 50px;
    }

    .choiceIn {
        padding: 0 25px;
    }

    .choiceIn select {
        height: 50px;
        width: 200px;
        font-size: 30px;
    }
    
</style>