<script setup>
import { ref, onMounted, computed } from 'vue'
import EventItem from './components/EventItem.vue'
import ShoppingBasket from './components/ShoppingBasket.vue'

const basket = ref([])

onMounted(async () => {
  try {
    const response = await fetch('/basket.json')
    const data = await response.json()
    const now = new Date()
    basket.value = data.filter((event) => new Date(event.date) >= now)
  } catch (error) {
    console.error('Error fetching basket data:', error)
  }
})

// Helper function to get all tickets from basket
const allTickets = computed(() =>
  basket.value.flatMap((event) => event.tickets)
)

// Total number of tickets in the basket
const totalTickets = computed(() =>
  allTickets.value.reduce((sum, ticket) => sum + ticket.quantity, 0)
)

// Total price of all tickets in the basket
const totalPrice = computed(() =>
  allTickets.value.reduce(
    (sum, ticket) => sum + ticket.price * ticket.quantity,
    0
  )
)

// Price of the cheapest ticket in the basket
const cheapestTicketPrice = computed(() => {
  const prices = allTickets.value.map((ticket) => ticket.price)
  return prices.length ? Math.min(...prices) : null
})
</script>

<template>
  <div class="container">
    <ul class="event-list">
      <EventItem v-for="event in basket" :key="event.name" :event />
    </ul>
    <h1>Shopping basket</h1>
    <ShoppingBasket :totalTickets :totalPrice :cheapestTicketPrice />
  </div>
</template>

<style scoped>
.container {
  padding: 8rem;
}

h1 {
  font-size: 2em;
}

.event-list {
  display: flex;
  flex-direction: column;
  list-style: none;
  gap: 20px;
  padding: 30px 0;
}

.event {
  background-color: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}
</style>
