<template>
  <AppLayout>
    <template #header>Header</template>
    <AppUserList>
      <template #secondrow="{item: user, remove}">
        <AppButton @click="remove(user)">remove</AppButton>
      </template>
    </AppUserList>
      <AppScoped :message2="message2">
        <template #test="{test2, test3}">
          Bonjour {{ test2 }} {{ test3 }}
        </template>
      </AppScoped>
    <template #footer>Footer</template>
  </AppLayout>
</template>

<script setup>
import AppButton from "@/components/AppButton";
import AppUserList from "@/components/AppUserList";
import AppLayout from "@/components/AppLayout";
import AppScoped from "@/components/AppScoped";
import { ref } from "vue";

const message2 = ref('Hello le père Doni !')
</script>

<style>
body {
  margin: 0;
  padding: 0;
}
</style>