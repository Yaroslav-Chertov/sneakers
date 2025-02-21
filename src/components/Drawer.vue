<script setup>
import DrawerHead from './DrawerHead.vue'
import CartItemList from './CartItemList.vue'
import InfoBlock from './InfoBlock.vue'

const emit = defineEmits(['createOrder'])

defineProps({
  totalPrice: Number,
  vatPrice: Number,
  buttonDisabled: Boolean,
})
</script>

<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-70"></div>
  <div class="bg-white h-full w-96 fixed right-0 top-0 z-20 p-8">
    <DrawerHead />

    <div v-if="!totalPrice" class="flex h-full items-center">
      <InfoBlock
        title="Корзина пустая"
        description="Добавьте хотя бы одну пару кроссовок, чтобы сделать заказ."
        imageUrl="/package-icon.png"
      />
    </div>

    <div v-else>
      <CartItemList />

      <div class="flex flex-col gap-4 mt-7">
        <div class="flex gap-2">
          <span>Итого:</span>
          <div class="flex-1 border-b border-dashed"></div>
          <b>{{ totalPrice }} руб.</b>
        </div>
        <div class="flex gap-2">
          <span>НДС 20%:</span>
          <div class="flex-1 border-b border-dashed"></div>
          <b>{{ vatPrice }} руб.</b>
        </div>
        <button
          @click="emit('createOrder')"
          :disabled="buttonDisabled"
          class="mt-4 bg-[#9a9ac1] w-full rounded-xl py-3 text-white hover:bg-[#65638b] transition active:bg-[#161a33] disabled:bg-slate-300 cursor-pointer"
        >
          Оформить заказ
        </button>
      </div>
    </div>
  </div>
</template>
