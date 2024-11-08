<script lang="ts" setup>
const props = defineProps({
  user: {
    type: Object,
    required: true,
  },
});
</script>

<template>
    <div>
        <label for="name">Name:</label>
        <input name="name" type="text" v-model="user.name"></input>
        <label for="email">Email:</label>
        <input name="email" type="text" v-model="user.email"></input>
    </div>
</template>

<style lang="scss" scoped>
div {
    display: flex;
    flex-direction: column;
    text-align: left;
}
</style>
