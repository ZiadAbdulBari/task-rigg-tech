<template>
  <main>
    <TableWrapper :head="['Category', 'Brand', 'Price', 'Action']">
      <TableRow v-for="product in state.products" :key="product.id">
        <TableData type="data" :value="product.category" />
        <TableData type="data" :value="product.brand" />
        <TableData type="data" :value="product.price.toString()" />
        <TableData type="action" :value="product.id.toString()" @deleteRow="removeRow" />
      </TableRow>
    </TableWrapper>
  </main>
</template>
<script>
import TableWrapper from '../components/Table/TableWrapper.vue'
import TableRow from '../components/Row/TableRow.vue'
import TableData from '../components/Data/TableData.vue'
import axios from 'axios'
import { onMounted } from 'vue'
import { reactive } from 'vue'
export default {
  components: {
    TableWrapper,
    TableRow,
    TableData
  },
  emits: [],
  setup() {
    const state = reactive({
      products: []
    })
    const getProduct = () => {
      const url = 'https://dummyjson.com/products?limit=10'
      axios
        .get(url)
        .then((response) => {
          if (response.status == 200) {
            state.products = response.data.products
          }
        })
        .catch((error) => {
          console.log(error)
        })
    }
    // get product id but emited the event.
    // Delete api is working. But it is not able to delete item from the list because of it is a demo api.
    // But when i hit the delete api with the product id, it returns isDeleted:true and I menually remove that product from product array.
    const removeRow = (id) => {
      axios
        .delete(`https://dummyjson.com/products/${id}`)
        .then((response) => {
          if (response.status == 200) {
            const filteredProduct = state.products.filter((product) => product.id != id)
            state.products = filteredProduct
          }
        })
        .catch((error) => {
          console.log(error)
        })
    }
    onMounted(() => {
      getProduct()
    })
    return {
      state,
      removeRow
    }
  }
}
</script>
