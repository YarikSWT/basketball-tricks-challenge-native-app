<template>
   <nb-container>
    <nb-header>
      <nb-left>
        <nb-button :onPress="goHome" transparent>
          <!-- <nb-icon :name="menu" /> -->
          <nb-icon name="home" />
        </nb-button>
      </nb-left>
      <nb-body>
        <nb-title>Basketball Tricks Game</nb-title>
      </nb-body>
      <nb-right />
    </nb-header>
    <nb-content padder>
      <view class="container">
        <!-- <button v-if="state > 0" :on-press="goHome" title="Go Home"></button> -->
        <view>
          <view v-if="state == 0">
            <!-- <nb-text class="text-color-primary">Basketball Tricks Game</nb-text> -->
            <nb-button class="start-btn" :on-press="startGame">
              <nb-text >Start</nb-text>
            </nb-button>
          </view>
          <GameAssets v-else></GameAssets>
        </view>
      </view>
    </nb-content>
    <!-- <nb-footer>
      <nb-footer-tab>
        <nb-button active full>
          <nb-text>Footer</nb-text>
        </nb-button>
      </nb-footer-tab>
    </nb-footer> -->
  </nb-container>
</template>

<script>

import GameAssets from "./components/GameAssets.vue"
import Vue from "vue-native-core";
import { VueNativeBase } from "native-base";
Vue.use(VueNativeBase);

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
  display: flex;
  flex-direction: column;
  height: 100%;
  width: 100%;
  /* top: 200px; */
  /* flex: ; */
}
.start-btn{
  top: 300px;
  /* margin-top: 50%; */
}
.text-color-primary {
  color: blue;
  margin-bottom: 100px;
  /* top: -100px; */
}
</style>
