<script setup>
import Card from '@/components/BasicCard.vue'
import { reactive, watchEffect } from 'vue'

const props = defineProps({
  backendOnline: Boolean,
})

const users = reactive({
  count: 0
})

const getUsers = async () => {
  if (!props.backendOnline) {
    return
  }

  await fetch(import.meta.env.VITE_BACKEND_URL + '/api/users-count')
    .then(async response => {
      users.count = await response.json()
    })
}

watchEffect(() => {
  getUsers()
})
</script>

<template>
  <Card class="flex-grow">
    <div class="flex items-center justify-between">
      <p class="basis-1/4 font-medium text-nowrap">Пользователи</p>
      <p v-if="props.backendOnline" class="flex-grow font-medium text-nowrap text-end">{{ users.count.toLocaleString('RU-ru') }}</p>
      <p v-if="!props.backendOnline" class="flex-grow font-light text-nowrap text-end text-red-500">Сервер недоступен</p>
    </div>
  </Card>
</template>

<style scoped>

</style>