<script setup>
import FoodCrad from './components/FoodCard.vue'
import { ref } from 'vue'

const foods = ref([
  { name: '寿司', emoji: '🍣' },
  { name: 'ハンバーガー', emoji: '🍔' },
  { name: '焼肉', emoji: '🥩' },
  { name: '麺系', emoji: '🍜' },
  { name: 'たこ焼き', emoji: '🐙' },
  { name: 'おでん', emoji: '🍢' },
  { name: '丼系', emoji: '🍚' },
  { name: 'オムライス', emoji: '🥚' },
  { name: 'イタリアン', emoji: '🇮🇹' },
  { name: '中華料理', emoji: '🇨🇳' },
  { name: 'とんかつ', emoji: '🐖' },
  { name: '韓国料理', emoji: '🇰🇷' },
  { name: 'カレー', emoji: '🍛' },
  { name: '鍋系', emoji: '🍲' },
  { name: '居酒屋', emoji: '🏮' },
  { name: 'ファミレス', emoji: '🍽️' },
])
const pickedFood = ref(0)
const newFood = ref(1)
function pickFood(index) {
  pickedFood.value = index
  newFood.value++
}
</script>

<template>
  <main>
    <h1 class="title">今日何食べる？</h1>
    <FoodCrad
      :name="foods[pickedFood].name"
      :emoji="foods[pickedFood].emoji"
      @click="pickFood(pickedFood)"
    />
    <template v-if="newFood < foods.length">
      <p>VS</p>
      <FoodCrad
        :name="foods[newFood].name"
        :emoji="foods[newFood].emoji"
        @click="pickFood(newFood)"
      />
    </template>
  </main>
</template>

<style scoped>
main {
  width: 350px;
  margin: 100px auto;
  text-align: center;
}

.title {
  margin-bottom: 60px;
}
</style>
