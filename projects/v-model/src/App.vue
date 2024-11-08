<script lang="ts" setup>
import { reactive } from 'vue'
import Profile from './components/Profile.vue'
import EditProfile from './components/EditProfile.vue'

const user = reactive({
  name: 'John Doe',
  email: 'test@test.com',
})
</script>
<template>
  <EditProfile :user="user" />
  <Profile :user />
</template>

<style lang="scss" scoped></style>
