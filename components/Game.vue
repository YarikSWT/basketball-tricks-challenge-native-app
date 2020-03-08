<template>
  <view class="window">
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
</template>

<script>
export default {
  props: ["amount"],
  data() {
    return {
      currentPlayer: 1,
      currentTask: "",
      tasks: ["Fadeaway", "T-jass layup", "Kyrie reverse layup", "Curry range"],
      scores: []
    };
  },
  created() {
    this.currentTask = this.tasks[
      Math.floor(Math.random() * this.tasks.length)
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
      this.currentTask = this.tasks[
        Math.floor(Math.random() * this.tasks.length)
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
      this.nextPlayer();
    }
  }
};
</script>

<style>
.h1{
    text-align: center;
    margin-top: -50px;
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
  width: 400px;
  display: flex;
  flex-direction: column;
  /* align-items: center */
  justify-content: center;
}
</style>
