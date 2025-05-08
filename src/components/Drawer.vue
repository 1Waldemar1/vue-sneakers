<script setup>
import CartItemList from './CartItemList.vue'
import DrawerHead from './DrawerHead.vue'
</script>

<template>
  <div class="fixed top-0 left-0 bg-black h-full w-full z-10 opacity-70"></div>
  <div class="bg-white w-96 h-full fixed flex flex-col right-0 top-0 z-20 p-8 overflow-auto">
    <DrawerHead />
    <CartItemList />
    <div class="flex flex-col gap-4 mt-7">
      <div class="flex gap-2">
        <span>Итого:</span>
        <div class="flex-1 border-b border-slate-400 border-dashed"></div>
        <b>12990 руб.</b>
      </div>
      <div class="flex gap-2">
        <span>Налог 5%:</span>
        <div class="flex-1 border-b border-slate-400 border-dashed"></div>
        <b>900 руб.</b>
      </div>
      <button
        disabled=""
        class="bg-lime-500 mt-4 w-full rounded-xl py-3 text-white disabled:bg-slate-300 hover:bg-lime-600 transition active:bg-lime-700 cursor-pointer"
      >
        Оформить заказ
      </button>
    </div>
  </div>
</template>
