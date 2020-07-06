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
    <nb-content padder > <!-- :style="{ backgroundImage: require('./assets/basket.png')}"  -->
     <image class="background" :source="require('./assets/basket.png')" alt=""/>
      <view class="container" >
        <!-- <button v-if="state > 0" :on-press="goHome" title="Go Home"></button> -->
        <view>
         
          <view v-if="state == 0" >
            
            <!-- <image class="background" :source="require('./assets/basket.png')" alt=""/> -->
            <!-- <nb-text class="text-color-primary">Basketball Tricks Game</nb-text> -->
            <nb-button class="start-btn" :on-press="startGame">
              <nb-text >Start</nb-text>
            </nb-button>
             <nb-button class="start-btn" :on-press="showRules">
              <nb-text >Game rules</nb-text>
            </nb-button>
             <nb-button class="start-btn" :on-press="goInstagram">
              <nb-text >Instagram</nb-text>
            </nb-button>
          </view>
          <GameAssets v-else></GameAssets>
        </view>
      </view>
    </nb-content>
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
    },
    showRules(){

    },
    goInstagram(){

    }
  },
}
</script>

<style>
.container {
  /* background-color: white; */
  align-items: center;
  justify-content: center;
  display: flex;
  flex-direction: column;
  height: 100%;
  width: 100%;
  /* background-image: url('./assets/basket.png'); */
  /* top: 200px; */
  /* flex: ; */
}
.start-btn{
  width: 220px;
  height: 44px;
  font-size: 24px;
  background-color: #2C42FF;
  top: 300px;
  margin-bottom: 20px;
  border-color: white;
  border-width: 1px;
  text-align: center;
  /* box-shadow: 0px 0px 25px rgba(255, 255, 255, 0.2); */
  border-radius: 18px;
  /* margin-top: 50%; */
}
.text-color-primary {
  color: blue;
  margin-bottom: 100px;
  /* top: -100px; */
}
.background{
  position: absolute;
  left: 0;
  top: 0;
  width: 105%;
  /* height: 530%; */
}
</style>
