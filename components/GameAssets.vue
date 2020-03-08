<template>
    
    <view v-if="!started">
        <text>Select amount of players</text>
         <text-input
            :style="{height: 40, width: 100, borderColor: 'gray', borderWidth: 1}"
            v-model="text"
         />
         <button :on-press="beginGame" title="Begin"></button>
    </view>
    <Game v-else :amount="text"></Game>
    
</template>

<script>
import Game from './Game.vue'

export default {
     components: {
        Game
    },
    data() {
        return {
            text: '',
            started: false
        };
    },
    methods: {
        beginGame(){
            this.started = true;
        },
        
    },
}
</script>