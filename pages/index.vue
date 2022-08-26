<template>
  <div class="d-flex justify-content-between p-5">
    <a class="alert alert-primary" href="/sidecharacter">Yan Karakterler</a>
    <Character
      :character="hero"
      :damage="villainDamage"
      @damage="heroDamage = $event"
      @healed="healedAmount = $event"
    />
    <Character
      :damage="heroDamage"
      :character="monster"
      :healed-amount="healedAmount"
      @damage="villainDamage = $event"
    />
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      hero: {
        name: 'Mario',
        power: 10,
        health: 100,
        role: 'hero'
      },
      monster: {
        name: 'Bowser',
        power: 8,
        health: 100,
        role: 'villain'
      },
      heroDamage: 0,
      villainDamage: 0,
      healedAmount: 0
    }
  }
}
</script>
