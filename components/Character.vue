<template>
  <div class="card" style="width: 18rem">
    <!-- <img class="card-img-top" src="..." alt="Card image cap" /> -->
    <div :style="{ width: characterHealth + '%' }" class="healthbar">
      {{ characterHealth }}
    </div>
    <div class="card-body">
      <h5 class="card-title">{{ character.name }}</h5>
      <p class="card-text">power : {{ character.power }}</p>
      <button
        v-if="character.role === 'hero'"
        href="#"
        class="btn btn-primary"
        @click="attack()"
      >
        Saldır
      </button>
      <button
        v-if="character.role === 'hero'"
        href="#"
        class="btn"
        style="background-color: green"
        @click="heal()"
      >
        İyileş
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CharacterComponent',
  props: {
    character: {
      type: Object,
      default: null
    },
    damage: {
      type: Number,
      default: 0
    },
    healedAmount: {
      type: Number,
      default: 0
    }
  },
  data() {
    return {
      characterHealth: this.character.health
    }
  },
  watch: {
    damage() {
      this.characterHealth -= this.damage
      if (this.character.role === 'villain') {
        this.attack()
      }
    },
    healedAmount() {
      this.attack(this.healedAmount)
    }
  },
  methods: {
    attack(heal) {
      if (heal) {
        const damageNumber = Math.floor(Math.random() * this.healedAmount + 3)
        this.$emit('damage', damageNumber)
      } else {
        const damageNumber = Math.floor(Math.random() * this.character.power)
        this.$emit('damage', damageNumber)
      }
    },
    heal() {
      const healNumber = Math.floor(Math.random() * this.character.power)
      if (this.characterHealth > 100) {
        this.characterHealth = 100
      } else {
        this.characterHealth += healNumber
      }
      this.$emit('healed', healNumber)
    }
  }
}
</script>

<style scoped>
.healthbar {
  height: 40px;
  background-color: green;
  color: rgb(139, 0, 0);
  
}
</style>
