<template>
  <div id="app">
    <sui-grid :columns="3">
      <sui-grid-row class="textYouAndMonster">
        <sui-grid-column class="paddingLeft">
          <h1>YOU</h1>
          <div class="marginLeft">
            <sui-progress
              color="green"
              :percent="playerHealth"
              progress
            />
          </div>
        </sui-grid-column>
        <sui-grid-column class="paddingRight">
          <h1>MONSTER</h1>
          <div class="marginRight">
            <sui-progress    
              color="green"
              :percent="monsterHealth"
              style="text-align:center;"
              progress
            />
          </div>
        </sui-grid-column>
      </sui-grid-row>
    </sui-grid>
    <div class="paddingSegment">
      <sui-segment>
        <section v-if="!gameIsRunning">
          <sui-button class="buttonStart" @click="startGame">
            START NEW GAME
          </sui-button>
        </section>
        <section v-else>
          <sui-button color="green" inverted @click="attack">
            ATTACK
          </sui-button> 
          <sui-button color="red" inverted @click="specialAttack">
            SPECIAL ATTACK
          </sui-button>
          <sui-button :style="{button: 'disabled'}" color="blue" inverted @click="heal">
            HEAL
          </sui-button>
          <sui-button color="yellow" inverted @click="giveUp">
            GIVE UP
          </sui-button>
        </section>
      </sui-segment>
      <sui-segment v-if="turns.length > 0">
        <th>
          <p v-for="(turn, index) in turns" :key="index">
            {{ turn.text }}
          </p>
        </th>
      </sui-segment>
    </div>
  </div>
</template>

<script>

export default {
  name: 'app',
  data() {
    return {
      playerHealth: 100,
      monsterHealth: 100,
      gameIsRunning: false,
      textAlign: 'left',
      buttonVisibleHeal: 'button',
      turns: []
    }
  },
  methods: {
    
  }
}
</script>

<style>
#app {
  /* font-family: 'Avenir', Helvetica, Arial, sans-serif; */
  /* -webkit-font-smoothing: antialiased; */
  /* -moz-osx-font-smoothing: grayscale; */
  text-align: center;
  /* color: #2c3e50; */
  margin-top: 60px;
}

.buttonStart {
  background-color:#35bdb2 !important;
  color:#fff !important;
}

.paddingLeft {
  margin-left: 12%;
}

.paddingRight {
  margin-left: 9%;
}

.paddingSegment {
  padding-left: 10%;
  padding-right: 10%;
}
</style>
