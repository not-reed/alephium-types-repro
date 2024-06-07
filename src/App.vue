<script setup lang="ts">
import { validateAddress, groupOfAddress, bs58 } from '@alephium/web3'
import { computed, ref } from 'vue';

const address = ref('')

const isValid = computed(() => {
  try {
    validateAddress(address.value)
    return true
  } catch (e) {
    return false
  }
})

const isContract = computed(() => {
  try {
    return isValid ? bs58.decode(address.value)[0] === 0x03 : false
  } catch {
    return false
  }
})
</script>

<template>
  <div class="grid justify-center items-center min-h-dvh bg-gradient-to-tl from-teal-700 to-indigo-500">

    <div class="grid gap-4 items-center justify-center">
      <div>
        <input v-model="address" placeholder="Enter an address"
          class="bg-neutral-400/15 px-4 py-2 shadow-xl text-xl rounded-xl" />
      </div>

      <div class="text-center text-xs opacity-50">
        Is {{ address.length > 8 ? `'${address.slice(0, 4)}...${address.slice(-4)}'` : address || '_____' }} a valid
        address?
      </div>


      <div class="flex items-center justify-center font-bold text-9xl">
        <div class="text-emerald-400" v-if="isValid">Yes</div>
        <div class="text-rose-400" v-else-if="address.length">No</div>
        <div v-else>&nbsp;</div>
      </div>

      <div v-if="isValid" class="grid grid-cols-2 gap-8">
        <div class="bg-neutral-400/15 px-4 py-2 shadow-xl rounded-xl">
          <div class="text-center text-xs opacity-50">
            Group
          </div>
          <div class="text-center text-2xl font-bold">
            {{ groupOfAddress(address) }}
          </div>
        </div>

        <div class="bg-neutral-400/15 px-4 py-2 shadow-xl rounded-xl">
          <div class="text-center text-xs opacity-50">
            Group
          </div>
          <div class="text-center text-2xl font-bold">
            {{ isContract ? "Contract" : 'Address' }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
