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
      <!--  -->
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
    }
  },
  methods: {
    startGame() {
      this.gameIsRunning = true
      this.playerHealth = 100
      this.monsterHealth = 100
      
    },
    attack() {
      var max = 3
      var min = 10
      var damage = Math.max(Math.floor(Math.random() * max) + 1, min)
      this.monsterHealth -= damage

      max = 3
      min = 10
      damage = Math.max(Math.floor(Math.random() * max) + 1, min)
      this.playerHealth -= damage
    },
    specialAttack() {
      var max = 10
      var min = 20
      var damage = Math.max(Math.floor(Math.random() * max) + 1, min)
      this.monsterHealth -= damage

      max = 10
      min = 20
      damage = Math.max(Math.floor(Math.random() * max) + 1, min)
      this.playerHealth -= damage
    },
    heal() {
      if (this.playerHealth <= 90) {
        this.playerHealth += 10;
      } else {
        this.playerHealth = 100;
      }
    },
    giveUp() {
      this.gameIsRunning = false
    }

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
