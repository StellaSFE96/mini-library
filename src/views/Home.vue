<template>
  <div class="home">
  <button class="list-button" @click="showList = true">Reading list</button>
    <h1>Classic Children’s books</h1>
    <div class="flex">
      <Readinglist v-if="showList" :readList="readList" @list="showList = false" @delete="removeBook"/>
      <Singlebook v-if="showModal" @modal="showModal = false" :clickedBook="clickedBook" @read="addToList"/>
      <Book1 v-for="book in books" :key="book.title" :book="book" @clicked="selectedBook"/>
    </div>
  </div>
</template>

<script>
import Book1 from '../components/Book1.vue'
import Singlebook from '../components/Singlebook.vue'
import Readinglist from '../components/Readinglist.vue'

export default {
  name: 'Home',
  components: {Book1, Singlebook, Readinglist},
  props: ['books'],
  methods:{
    selectedBook(book){
      this.clickedBook = book
      this.showModal = true
    },
    addToList(listItem){
     if(this.readList.find((book) => book.title == listItem.title)){
       return
    }
    this.readList.push(listItem)
},

  removeBook(book){
    console.log("mamma")
    for(let i = 0; i < this.readList.length; i++){
        if(book.title == this.readList[i].title) {
          this.readList.splice(i, 1)
      } 
    }
  }
},

  data(){return{
    showModal: false,
    clickedBook: {},
    readList:[],
    showList: false
  }}
}
</script>

<style scoped>

.flex{
  display: flex;
  flex-direction: row;
  margin: 10px;
  flex-wrap: wrap;
}

h1{
  margin-left: 40px;
}

.list-button{
  background-color: black;
  color: white;
  border-radius: 5px;
  width: 120px;
}

</style>
