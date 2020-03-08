<template>
  <view class="container">
    <button v-if="state > 0" :on-press="goHome" title="Go Home"></button>
    <view>
      <view v-if="state == 0">
        <text class="text-color-primary">Basketball Tricks Game</text>
        <button :on-press="startGame" title="Start"></button>
      </view>
      <GameAssets v-else></GameAssets>
    </view>
  </view>
</template>

<script>
// import MintUI from 'mint-ui'
import GameAssets from "./components/GameAssets.vue"
export default {
  components: {
    GameAssets
  },
  data() {
    return {
      state: 0
    }
  },
  methods: {
    startGame(){
      this.state = 1
    },
    goHome(){
      this.state = 0
    }
  },
}
</script>

<style>
.container {
  background-color: white;
  align-items: center;
  justify-content: center;
  flex: 1;
}
.text-color-primary {
  color: blue;
  top: -100px;
}
</style>
