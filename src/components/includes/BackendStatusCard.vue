<script async setup>
import Card from '@/components/BasicCard.vue'
import Badge from '@/components/ui/PillDotBadge.vue'
import { onMounted, ref } from 'vue'

const backend = ref({
  status: 'default',
  message: 'Waiting'
})

const requestStatus = async () => {
  await fetch(import.meta.env.VITE_BACKEND_URL + '/api/status')
    .then(response => {
      if (response.status !== 200) {
        backend.value.message = 'Error (' + response.status + ')'
        backend.value.status = 'error'
        emit('statusChanged', { value: false })
        return
      }

      backend.value.message = 'Online'
      backend.value.status = 'success'
      emit('statusChanged', { value: true })
    })
    .catch(() => {
      backend.value.message = 'Offline'
      backend.value.status = 'error'
      emit('statusChanged', { value: false })
    })
}

const emit = defineEmits(['statusChanged'])

onMounted(() => {
  requestStatus()
  setInterval(requestStatus, 3000)
})
</script>

<template>
  <Card>
    <div class="flex space-x-3 items-center justify-between">
      <p class="font-medium text-nowrap">Статус сервера</p>
      <Badge :type="backend.status">{{ backend.message }}</Badge>
    </div>
  </Card>
</template>

<style scoped>

</style>