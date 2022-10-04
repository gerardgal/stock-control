<template>
  <q-page class="flex flex-center" padding>
    <div>
      <StockItem></StockItem>
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import StockItem from '../components/StockItem.vue'

export default defineComponent({
  name: 'IndexPage',
  components: {
    StockItem
  },
})
</script>
