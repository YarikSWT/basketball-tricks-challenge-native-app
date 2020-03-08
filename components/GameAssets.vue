<template>
  <view v-if="!started">
    <nb-h1 class="h1">Select amount of players</nb-h1>
    <nb-h2 class="h2">and MODE</nb-h2>
    <nb-form class="form">
      <nb-item class="form-item" floatingLabel>
        <nb-label>Write amunt of players</nb-label>
        <nb-input keyboardType="numeric" v-model="numPlayers" />
      </nb-item>
      <nb-item picker>
        <nb-picker
          mode="dropdown"
          :selectedValue="selectedMode"
          placeholder="Select MODE"
          placeholderStyle="{ color: '#bfc6ea' }"
          placeholderIconColor="#007aff"
          :onValueChange="onValueChange"
        >
          <item label="Easy" value="key0" />
          <item label="Medium" value="key1" />
          <item label="Hard" value="key2" />
          <item label="Random" value="key3" />
        </nb-picker>
      </nb-item>
    </nb-form>
    <nb-button :disabled="numPlayers == '' || selectedMode == '' " :on-press="beginGame"> <nb-text class="btn-text">Begin</nb-text> </nb-button>
  </view>
  <Game v-else :amount="numPlayers" :mode="selectedMode"></Game>
</template>

<script>
import Game from "./Game.vue";
import React from "react";
import { Picker, Icon } from "native-base";

export default {
  components: {
    Game
  },
  data() {
    return {
      numPlayers: "",
      selectedMode: "",
      started: false
    };
  },
  methods: {
    beginGame() {
      this.started = true;
    },
    onValueChange: function(value) {
      this.selectedMode = value;
    },
    // getIosIcon: function() {
    //   return <Icon name="ios-arrow-down-outline" />;
    // }
  }
};
</script>

<style>
.h2 {
  margin-bottom: 30px;
  text-align: center;
}
.form{
    margin-bottom: 50px;
}
.btn-text{
    text-align: center;
}
.form-item{
    margin-bottom: 30px;
}
</style>
