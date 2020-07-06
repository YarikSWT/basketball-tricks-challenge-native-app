<template>
  <view class="window" v-if="!final">
      <nb-h1 class="h1">Player {{ currentPlayer }}</nb-h1>
    <!-- <text>Player {{ currentPlayer }}</text> -->
    <view>
      <nb-card class="card">
        <nb-card-item header>
          <nb-text>Task</nb-text>
        </nb-card-item>
        <nb-card-item>
          <nb-body>
            <nb-text>
              {{ currentTask }}
            </nb-text>
          </nb-body>
        </nb-card-item> 
      </nb-card>
    </view>
    <view class="buttons">
      <nb-button rounded danger :on-press="notScored">
        <nb-text>+0</nb-text>
      </nb-button>
      <nb-button rounded success :on-press="scored">
        <nb-text>+1</nb-text>
      </nb-button>
      <!-- <button :on-press="notScored" title="x"></button>
            <button :on-press="scored" title="o"></button> -->
    </view>
    <view>
      <text>Score:</text>
      <text v-for="(score, id) in scores" :key="'score_' + id">
        <text>{{ score.player + 1 }} = {{ score.score }}</text>
      </text>
    </view>
  </view>
  <view v-else>
      <nb-h1 class="h1">Player {{ currentPlayer }} WIN</nb-h1>
  </view>
</template>

<script>
export default {
  props: ["amount","mode", "end"],
  data() {
    return {
      currentPlayer: 1,
      currentTask: "",
      tasks: { 
          hard: ["Fadeaway", "T-jass layup", "Kyrie reverse layup", "Curry range"],
          medium: ["fuck Igor"],
          easy: ["fuck Yarik"],
          random: ["Fadeaway", "T-jass layup", "Kyrie reverse layup", "Curry range", "fuck Igor", "fuck Yarik"]
          },
      scores: [],
      final: false
    };
  },
  created() {
    console.log(this.mode, this.tasks[this.mode], this.end)
    this.currentTask = this.tasks[this.mode][
      Math.floor(Math.random() * this.tasks[this.mode].length)
    ];
    for (let index = 0; index < this.amount; index++) {
      this.scores.push({
        player: index,
        score: 0
      });
    }
  },
  methods: {
    nextPlayer() {
      this.currentTask = this.tasks[this.mode][
        Math.floor(Math.random() * this.tasks[this.mode].length)
      ];
      this.currentPlayer += 1;
      if (this.currentPlayer > this.amount) this.currentPlayer = 1;
    },
    notScored() {
      this.scores[this.currentPlayer - 1].score += 0;
      this.nextPlayer();
    },
    scored() {
      this.scores[this.currentPlayer - 1].score += 1;
      if(this.scores[this.currentPlayer - 1].score >= this.end){
        //   console.log(this.scores[this.currentPlayer - 1])
          this.final = true
      }else
        this.nextPlayer();
    }
  }
};
</script>

<style>
.h1{
    text-align: center;
    /* margin-top: -50px; */
    margin-bottom: 40px;
}
.buttons {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  margin-bottom: 70px;
}
.card{
    margin-bottom: 40px;
}
.window {
  width: 300px;
  display: flex;
  flex-direction: column;
  /* align-items: center */
  justify-content: center;
}
</style>
