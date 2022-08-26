<template>
  <div class="d-flex justify-content-between p-5">
    <a class="alert alert-primary" href="/">Ana Sayfa</a>
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
        name: 'Bulbasaur',
        power: 10,
        health: 120,
        role: 'hero'
      },
      monster: {
        name: 'Rattata',
        power: 15,
        health: 90,
        role: 'villain'
      },
      heroDamage: 0,
      villainDamage: 0,
      healedAmount: 0
    }
  }
}
</script>