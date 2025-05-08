<script setup>
import axios from 'axios'
import { onMounted, ref, watch } from 'vue'
import CardList from './components/CardList.vue'
import Header from './components/Header.vue'

const items = ref([])
const sortBy = ref('')
const searchQuery = ref('')

const onChangeSelect = (event) => {
  sortBy.value = event.target.value
}

onMounted(async () => {
  try {
    const { data } = await axios.get('https://23e8abceb6dd1d83.mokky.dev/items')
    items.value = data
  } catch (err) {
    console.log(err)
  }
})

watch(sortBy, async () => {
  try {
    const { data } = await axios.get(
      'https://23e8abceb6dd1d83.mokky.dev/items?sortBy=' + sortBy.value,
    )
    items.value = data
  } catch (err) {
    console.log(err)
  }
})
</script>
<template>
  <!-- <Drawer /> -->
  <div class="w-4/5 m-auto bg-white rounded-xl shadow-xl mt-14">
    <Header />
    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>

        <div class="flex gap-4">
          <select
            @change="onChangeSelect"
            class="py-2 px-3 border border-gray-400 text-gray-900 rounded-md outline-none hover:border-gray-600"
            name=""
            id=""
          >
            <option value="name">По названию</option>
            <option value="price">По цене (дешевые)</option>
            <option value="-price">По цене (дорогие)</option>
          </select>

          <div class="relative">
            <img class="absolute left-4 top-3" src="/search.svg" alt="Search" />
            <input
              class="border border-gray-400 text-gray-900 rounded-md py-2 pl-11 pr-4 outline-none focus:border-gray-600"
              placeholder="Поиск..."
              type="text"
            />
          </div>
        </div>
      </div>
      <div class="mt-10">
        <CardList :items="items" />
      </div>
    </div>
  </div>
</template>
