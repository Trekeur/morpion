<script>
import Button from 'primevue/button';

export default {
    name: 'AppHeader',
    data: function () {
        let grid = Array(9)
        // for (let i = 0; i < array.length; i++) {

        //     grid[i] = ""
        // }
        grid["bot-left"] = ""
        grid["bot-middle"] = ""
        grid["bot-right"] = ""
        grid["middle-left"] = ""
        grid["middle-middle"] = ""
        grid["middle-right"] = ""
        grid["top-left"] = ""
        grid["top-middle"] = ""
        grid["top-right"] = ""
        return { winner: " ", count: 0, grid }
    },

    methods: {
        winnerEvent(event) {
            this.count++
            if (this.count%2 == 0) {
                this.grid[event.target.id] = "X"
            }
            else {
                this.grid[event.target.id] = "O"
            }
            console.log(this.grid[event.target.id])

            if (
                (this.grid["top-left"] === this.grid["top-middle"]    && this.grid["top-middle"]    === grid["top-right"] && this.grid["top-left"] != "") ||
                (this.grid["top-left"] === this.grid["middle-middle"] && this.grid["middle-middle"] === grid["bot-right"] && this.grid["top-left"] != "") ||
                (this.grid["top-left"] === this.grid["middle-left"]   && this.grid["middle-left"]   === grid["bot-left"] && this.grid["top-left"] != "") ||
                //--
                (this.grid["middle-middle"] === this.gird["middle-left"] && this.grid["middle-middle"] === grid["middle-right"] && this.grid["middle-middle"] != "") ||
                (this.grid["middle-middle"] === this.gird["middle-top"]  && this.grid["middle-middle"] === grid["middle-bot"] && this.grid["middle-middle"] != "") ||
                //--
                (this.grid["bot-right"] === this.grid["bot-middle"]    && this.grid["bot-middle"]    === this.grid["bot-left"] && this.grid["bot-right"] != "") ||
                (this.grid["bot-left"]  === this.grid["middle-middle"] && this.grid["middle-middle"] === this.grid["top-right"] && this.grid["bot-right"] != "") ||
                (this.grid["bot-right"] === this.grid["middle-right"]  && this.grid["middle-right"]  === this.grid["top-right"] && this.grid["bot-right"] != "")

            ) {
                this.winner = this.grid[event.target.id]
                this.grid = null
            }
        }

    }
}

</script>

<template>


        <div id="Jeu">
            <div>
                <button class="button" id="top-left"   @click="winnerEvent($event)"> {{ this.grid["top-left"] }} </button>
                <button class="button" id="top-middle" @click="winnerEvent($event)"> {{ this.grid["top-middle"] }}</button>
                <button class="button" id="top-right"  @click="winnerEvent($event)"> {{ grid["top-right"] }} </button>
            </div>
            <div>
                <button class="button" id="middle-left"   @click="winnerEvent($event)">{{ this.grid["middle-left"] }}</button>
                <button class="button" id="middle-middle" @click="winnerEvent($event)">{{ this.grid["middle-middle"] }}</button>
                <button class="button" id="middle-right"  @click="winnerEvent($event)">{{ this.grid["middle-right"] }}</button>
            </div>
            <div>
                <button class="button" id="bot-left"   @click="winnerEvent($event)">{{ this.grid["bot-left"] }}</button>
                <button class="button" id="bot-middle" @click="winnerEvent($event)">{{ this.grid["bot-middle"] }}</button>
                <button class="button" id="bot-right"  @click="winnerEvent($event)">{{ this.grid["bot-right"] }}</button>
            </div>
        </div>
</template>

<style scoped>
body {
    background-color: LightSteelBlue;
    text-align: center;
    display: flex;
}
.button{
    border: 1px solid rgba(0, 0, 0, 0.8);
    font-size: 15px;
    background-color: green;
}

#Jeu {
    width: 500px;
    height: 500px;
    background-color: SteelBlue;
    margin: auto;
    padding: 10px;
    background-image: url("../assets/fond.jpg");

}

#Jeu div {
    margin: 0 auto;
    overflow: hidden;
}

#Jeu button {
    width: 100px;
    height: 100px;
    font-weight: bold;
    font-size: 50px;
    margin: 5px;
    float: left;
}
</style>