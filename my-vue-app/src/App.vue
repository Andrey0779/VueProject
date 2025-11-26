<script setup lang="ts">
import { ref, reactive } from 'vue'

const color = ref('red')
const headerClass = ref('r')

const users = reactive([
  { name: 'Вася', age: 30 },
  { name: 'Петя', age: 25 },
  { name: 'Ольга', age: 27 },
  { name: 'Игорь', age: 24 },
])

const textButton1 = ref('Скрыть список')
const showAllFlag = ref(true)

const showAgeFlag = ref(false)
const textButton = ref('Показать возраст')

function showHideAge() {
  showAgeFlag.value = !showAgeFlag.value
  if (showAgeFlag.value) {
    textButton.value = 'Скрыть возраст'
  } else textButton.value = 'Показать возраст'
}

function showHideAll() {
  showAllFlag.value = !showAllFlag.value
  if (showAllFlag.value) {
    textButton1.value = 'Скрыть список'
  } else textButton1.value = 'Показать список'
}

function changeColor() {
  if (headerClass.value == 'r') {
    color.value = 'green'
    headerClass.value = 'g'
  } else {
    color.value = 'red'
    headerClass.value = 'r'
  }
}
</script>

<template>
  <div>
    <div>
      <button @click="showHideAll()">{{ textButton1 }}</button>
    </div>
    <div v-show="showAllFlag">
      <button @click="showHideAge()">{{ textButton }}</button>
      <h1 @click="changeColor()" :class="{ green: headerClass === 'g', red: headerClass === 'r' }">
        <div v-for="(item, i) in users">
          {{ i }} - {{ item.name }} <span v-show="showAgeFlag">{{ item.age }}</span>
        </div>
      </h1>
    </div>
  </div>
</template>

<style scoped>
.red {
  color: red;
}
.green {
  color: green;
}
</style>
