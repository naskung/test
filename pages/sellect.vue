<template>
    <section>
      <div v-for="(fruit, index) in fruits" :key="fruit.id" @click="toggleEat(index)">
        <span :class="{ 'was-eaten': fruit.eaten }">{{ fruit.name }}</span>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    name: 'ToggleFruits',
    data() {
      return {
        fruits: [
          { id: 1, name: 'banana', eaten: false },
          { id: 2, name: 'apple', eaten: true },
          { id: 3, name: 'watermelon', eaten: false },
        ],
      }
    },
    methods: {
      toggleEat(clickedFruitIndex) {
        this.fruits = this.fruits.map((fruit) => ({
          ...fruit,
          eaten: false,
        }))
        return this.$set(this.fruits, clickedFruitIndex, {
          ...this.fruits[clickedFruitIndex],
          eaten: true,
        })
      },
    },
  }
  </script>

<style scoped>
.was-eaten {
  color: hsl(24, 81.7%, 49.2%);
}
</style>