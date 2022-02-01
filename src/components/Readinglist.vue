<template>
    <div class="modal" @click.self="$emit('list')">
        <div class="modal-content">
        <span @click="$emit('list')">&larr;</span>
            <h1>Reading List</h1>
            <div class="background">
                <ul>
                <li v-for="book in printList" :key="book.title">
                    <div class="flex">
                        <h3>{{book.title}}</h3>
                        <p>By {{book.author}}</p>
                    </div>
                    <p class="remove" @click="remove(book)">remove</p>
                </li>
            </ul>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props:['readList'],
    methods:{
        remove(book){
            this.$emit('delete', {...book})
        }
    },
    computed:{
        printList(){
            return this.readList
        }
    },
    data(){return{

    }}
}
</script>

<style lang="scss" scoped>

span{
    color: rgb(43, 40, 40);
    font-size: 2rem;
    background:rgb(194, 191, 191);
    border-radius: 50%;
    padding:2px;
     cursor: pointer;
}

.modal {
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%; 
  height: 100%; 
  overflow: auto; 
  background-color: rgb(0,0,0); 
  background-color: rgba(0,0,0,0.8); 
}

.modal-content {
  background-color: #fefefe;
  margin: 15% auto; 
  padding: 20px;
  width: 40%; 
  background: rgb(41, 40, 40);
  color: white;
  position: relative;
  border-radius: 10px;
}

h1{
    margin: 0;
}

.flex{
    display: flex;
     align-items: center;
    text-align: center;
}

.remove{
    color: rgb(129, 126, 126);
    font-size: .9rem;
     cursor: pointer;
}

ul{
    padding: .5rem;
}


li{
    display: flex;
    justify-content: space-between;
    align-items: center;
    text-align: center;
    border-bottom: 1px solid white;
    
    h3{
        margin: 0 10px 0 0;
    }
}

.background{
    background-color: rgb(63, 62, 62);
    border-radius: 10px;
}
</style>