<template>
  <div class="home">
    <Book1 v-for="book in books" :key="book.title" :book="book"/>
  </div>
</template>

<script>
import Book1 from '../components/Book1.vue'

export default {
  name: 'Home',
  components: {Book1},
  props: ['books']

}
</script>

<style scoped>

.home{
  display: flex;
  flex-direction: row;
  margin: 10px;
  flex-wrap: wrap;
}

</style>
