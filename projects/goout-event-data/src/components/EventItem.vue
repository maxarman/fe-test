<script setup>
import { computed, defineProps } from 'vue'

const props = defineProps(['event'])

const formattedDate = computed(() => {
  const date = new Date(props.event.date)
  return date.toLocaleDateString('cz-CZ', {
    day: 'numeric',
    month: 'numeric',
    year: 'numeric',
  })
})
</script>

<template>
  <li class="event">
    <div class="main-event">
      <h2>{{ event.name }}</h2>
      <p>{{ formattedDate }}</p>
    </div>

    <!-- Recursive rendering for sub-events -->
    <ul class="subevent-list">
      <li v-for="ticket in event.tickets" :key="ticket.ticketId">
        <p>Type: {{ ticket.name }}</p>
        <p>Quantity: {{ ticket.quantity }}</p>
        <p>Price: {{ ticket.price }}{{ ticket.currency }}</p>
        <br />
      </li>
    </ul>
  </li>
</template>

<style scoped>
.event {
  background-color: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  margin-bottom: 10px;
}

.main-event {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.subevent-list {
  margin-top: 10px;
  .event {
    background-color: rgba(180, 180, 180, 0.3);
    border-left: 15px solid gray;
  }
}

h2 {
  font-size: 1.5em;
  margin: 0;
}

p {
  font-size: 0.9em;
  color: #777;
}
</style>
