<template>
    <div>
        <h4>I'm a component :D</h4>
    </div>
</template>
  
<script>
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'StockItem',
    data() {
        return {
            items: [
                {
                    id: 1,
                    name: "Item 1",
                    category: "Category 1",
                    quantity: 5
                },
            ]
        }
    }
})
</script>