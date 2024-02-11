<script setup>
import PageContainer from '@/components/PageContainer.vue'
import Card from '@/components/BasicCard.vue'
import Badge from '@/components/ui/PillDotBadge.vue'
</script>

<template>
  <PageContainer class="space-y-3">
    <Card>
      <h1 class="text-xl font-bold mb-3">Демо-проект "Родственники"</h1>
      <p class="font-light text-md">
        На некотором сервисе зарегистрировано N пользователей.<br>
        Каждый пользователь при регистрации указал фамилию, имя и город.<br>
        Необходимо вывести список "родственников" в таблицу с указанием фамилии, города и количества пользователей с такой же фамилией.
      </p>
      <div class="mt-3">
        <a href="https://github.com/NikitaGaidai/vue-js-test-frontend" target="_blank" class="text-md font-semibold">
          Репозиторий на GitHub <span aria-hidden="true">→</span>
        </a>
      </div>
    </Card>
    <div class="flex flex-col space-y-3 md:flex-row md:space-x-3 md:space-y-0">
      <div class="basis-1/4 space-y-3">
        <Card>
          <div class="flex space-x-3 items-center justify-between">
            <p class="font-medium text-nowrap">Backend Status</p>
            <Badge type="success">Online</Badge>
          </div>
        </Card>
        <Card>
          <p>Пользователей в БД:</p>
        </Card>
      </div>
      <div class="flex-grow">
        <Card>
          Data
        </Card>
      </div>
    </div>
    <footer>
      <div class="mx-auto px-6 py-3 lg:px-8">
        <div class="mt-3">
          <p class="text-center text-xs leading-5 text-gray-600">
            &copy; {{ new Date().getFullYear() }} Nikita Gaidai. All rights reserved.
          </p>
        </div>
      </div>
    </footer>
  </PageContainer>
</template>

<style scoped>

</style>
