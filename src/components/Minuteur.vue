<template>
    <h1>Minuteur</h1>

    <div id="time" v-if="choice">
        <div id="timeTime">
            <p>{{hour}}</p><p>:</p><p>{{minute}}</p><p>:</p><p>{{seconde}}</p>
        </div>
        <button v-on:click="stop" id="stopButton">STOP</button>
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

    <div id="finish" v-if="this.finishPopUp">
        <h2>FINISH</h2>
        <button v-on:click="finish" v-if="this.finishPopUp">Fermer</button>
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
        numbers: [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,58,59],
        finishPopUp: false,
      }
    },
    methods: {
        go() {
            if(this.seconde != 404 && this.minute != 404) {
                this.choice = true
                let interMinu = setInterval(() => {
                    if(this.seconde > 0) {
                        this.seconde--;
                    } else if(this.minute > 0) {
                        this.seconde = 59;
                        this.minute--;
                    } else {
                        console.log('FINISH')
                        this.choice = false
                        clearInterval(interMinu)
                        this.finishPopUp = true
                    }
                }, 1000);
            }
        },

        stop() {
            console.log("stop")
            this.minute = 0;
            this.seconde = 0;
        },

        finish() {
            this.finishPopUp = false
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
        width: 80%;
        margin: 0 auto;
    }

    #stopButton {
        width: 200px;
        height: 50px;
    }

    #timeTime {
        display: flex;
        justify-content: space-around;
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

    #finish {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        position: absolute;
        top: 25%;
        left: 25%;
        background-color: grey;
        width: 50%;
        height: 50%;
    }
    
</style>