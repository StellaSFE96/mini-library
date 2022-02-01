<template>
    <div class="modal" @click.self="$emit('modal')">
    <div class="modal-content">
        <span @click="$emit('modal')">&larr;</span>
        <div class="flex">
            <article :style="clickedBook">
                <div class="line"></div>
                <h1>{{clickedBook.title}}</h1>
                <p>By {{clickedBook.author}}</p>
            </article>
            <div class="text-content">
                <h1>{{clickedBook.title}}</h1>
                <h2>By {{clickedBook.author}}</h2>
                <p>{{clickedBook.plot}}</p>
                <div class="book-facts">
                    <p><b>Audience:</b> {{clickedBook.audience}} </p>
                    <p><b>First published:</b> {{clickedBook.year}} </p>
                    <p><b>Pages:</b> {{clickedBook.pages}} </p>
                    <p><b>Publisher:</b> {{clickedBook.publisher}} </p>
                </div>
            <button @click="addToList">Oh, I want to read it!</button>
        </div>
        </div>

    </div>
    </div>


</template>

<script>
export default {
    props:{clickedBook:Object},
    methods:{
        addToList(){
            this.$emit('read', {...this.clickedBook})
        }
    }
}
</script>

<style lang="scss" scoped>

span{
    color: rgb(43, 40, 40);
    font-size: 2rem;
    cursor: pointer;
    background:rgb(194, 191, 191);
    border-radius: 50%;
    padding:2px;
}

.flex{
    display: flex;
    padding-top: 1.5rem;
    margin-bottom: 1.5rem;
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

/* Modal Content/Box */
.modal-content {
  background-color: #fefefe;
  margin: 15% auto; /* 15% from the top and centered */
  padding: 20px;
  width: 45%; /* Could be more or less, depending on screen size */
//   display: flex;
  background: rgb(41, 40, 40);
  position: relative;
  border-radius: 10px;
}
.text-content{
    width: 400px;
    color: white;

        h1{
            margin: 0;
        }

}
.book-facts{
    display: grid;
    grid-template-columns: repeat(2,1fr);
    column-gap: 10px;
    row-gap:1px;
    background: rgb(63, 62, 62);
    padding-left: 1rem;

    p{
        margin:5px 0;
    }
}

button{
    margin-top: 1rem;
}

article {
    width: 250px;
    height: 365px;
    background-color: rgb(72, 142, 221);
    margin-right: 30px;
    border-radius: 3px;
    position: relative;
    box-shadow: -20px 30px 70px -40px rgba(255,255,255,0.75) inset;

     h1{
        color: black;
        font-size: 1.2rem;
        margin-left: 25px;
        position: absolute;
        bottom: 30px;
    }

    p{
        color: black;
        font-size: 1rem;
        margin-left: 25px;
        position: absolute;
        bottom: 5px;
    }
}

.line{
    height: 365px;
    border-left: 3.5px solid rgb(121, 117, 117);
    margin-left: 9px;
    }

</style>