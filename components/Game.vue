<template>
    <view>
        <text>Player {{currentPlayer}}</text>
        <view>
             <text>Task: {{currentTask}}</text>
             <!-- <text>{{currentTask}}</text> -->
        </view>
        <view class="buttons">
            <button :on-press="notScored" title="x"></button>
            <button :on-press="scored" title="o"></button>
        </view>
        <view>
             <text>Score:</text>
             <text v-for="(score, id) in scores" :key="'score_' + id">
                 <text>{{score.player + 1}} = {{score.score}}</text>
             </text>
        </view>
    </view>
</template>

<script>
export default {
    props: ['amount'],
    data(){
        return{
            currentPlayer: 1,
            currentTask: "",
            tasks: [
                'Fadeaway',
                'T-jass layup',
                'Kyrie reverse layup',
                'Curry range'
            ],
            scores: []
        }
    },
    created() {
        this.currentTask = this.tasks[Math.floor(Math.random() * this.tasks.length)]
        for (let index = 0; index < this.amount; index++) {
            this.scores.push({
                player: index,
                score: 0
            })
        }
    },
    methods: {
        nextPlayer(){
            this.currentTask = this.tasks[Math.floor(Math.random() * this.tasks.length)]
            this.currentPlayer += 1
            if(this.currentPlayer > this.amount) this.currentPlayer = 1
        },
        notScored(){
            this.scores[this.currentPlayer - 1].score += 0
            this.nextPlayer();
        },
        scored(){
            this.scores[this.currentPlayer - 1].score += 1
            this.nextPlayer();
        }
    },

}
</script>

<style>
    .buttons{
        display: flex;
    }
</style>