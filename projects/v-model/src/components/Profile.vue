<script lang="ts" setup>
import { defineProps } from 'vue'

const props = defineProps({
  user: {
    type: Object,
    required: true,
  },
})
</script>

<template>
  <p>Name: {{ user.name }}</p>
  <!-- Name -->
  <p>Email: {{ user.email }}</p>
  <!-- Email -->
</template>

<style lang="scss" scoped></style>
