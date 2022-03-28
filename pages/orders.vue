<template>
    <div>
        <ul>
            <Order v-bind:sales="sales" />
        </ul>
    </div>
</template>

<script>
import Order from '@/components/Order'

export default {
  components: {Order},
  async fetch({store}) {
    await store.dispatch('orders/fetch')
  },
  computed: {
    sales() {
        return this.$store.getters['orders/sales'];
    }
  }
}
</script>