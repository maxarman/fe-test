<script setup>
const props = defineProps(['totalTickets', 'totalPrice', 'cheapestTicketPrice'])
</script>

<template>
  <div>
    <p>Number of tickets: {{ totalTickets }}</p>
    <p>Total price: {{ totalPrice }}</p>
    <p>Price of cheapest ticket: {{ cheapestTicketPrice }}</p>
  </div>
</template>

<style scoped></style>
