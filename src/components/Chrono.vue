<template>
    <h1>Chronometre</h1>
    <div id="time">
        <p>{{hour}}</p><p>:</p><p>{{minute}}</p><p>:</p><p>{{seconde}}</p>
    </div>
    <div id="choice">
        <button v-on:click="go()">GO</button>
        <button v-on:click="stop()" v-if="stopButton">STOP</button>
        <button v-on:click="reset()" v-if="resetButton">RESET</button>
    </div>
</template>

<script>
export default {
    name: 'Chrono',
    data() {
      return {
        seconde: 0,
        minute: 0,
        hour: 0,
        isRuning: false,
        stoping: false,
        stopButton: false,
        resetButton: false,
      }
    },
    methods: {
      go() {
          if(this.isRuning === false) {
                var inter = setInterval(() => {
                    if(this.stoping) {
                        clearInterval(inter)
                        this.stoping = false
                        this.isRuning = false
                        console.log(this.stoping)
                    } else {
                        this.seconde++
                        if(this.seconde > 59) {
                            this.seconde = 0
                            this.minute++
                        }
                        if(this.minute > 59) {
                            this.minute = 0
                            this.hour++
                        }
                    }
                }, 1000);
            this.isRuning = true;
            this.stopButton = true;
          }
      },

      stop() {
          if(this.stoping === false) {
              this.stoping = true
          }
          this.stopButton = false
          this.resetButton = true
      },

      reset() {
          this.stoping = false
          this.isRuning = false
          this.minute = 0
          this.seconde = 0
          this.hour = 0
          this.resetButton = false
      },
    }
}
</script>

<style scoped>
    h1{
        font-size: 60px;
        font-family: "poppins";
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
        margin: 0 auto;
        width: 50%;
        display: flex;
        justify-content: space-between;
    }

    #choice button {
        height: 100px;
        width: 100px;
        font-family: "poppins";
        background-color: white;
        border: none;
        border-radius: 50%;
        cursor: pointer;
    }

    #choice button:first-child {
        background-color: green;
        color: white;
    }

    #choice button:first-child:hover {
        background-color: rgb(0, 155, 0);
        transition: 0.2s;
    }

    #choice button:nth-child(2) {
        background-color: rgb(155, 0, 0);
        color: white;
    }

    #choice button:nth-child(2):hover {
        background-color: rgb(179, 0, 0);
    }
</style>