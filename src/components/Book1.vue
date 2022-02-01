<template>
    <div class="book">
        <article>
            <div class="line"></div>
            <h1>{{book.title}}</h1>
            <p>{{book.author}}</p>       
         </article>  
    </div>
</template>

<script>
export default {
name: 'Book1',
props: ['book']
}
</script>

<style lang="scss" scoped>

.book {
    width: 210px;
    max-height: 270px;
    background-color: rgb(72, 142, 221);
    margin: 30px;
    border-radius: 3px;
    position: relative;
    box-shadow: -20px 30px 70px -40px rgba(255,255,255,0.75) inset;

     h1{
        color: white;
        font-size: 1.2rem;
        margin-left: 25px;
        position: absolute;
        bottom: 30px;
    }

    p{
        color: white;
        font-size: 1rem;
        margin-left: 25px;
        position: absolute;
        bottom: 5px;
    }
}

.line{
    height: 270px;
    border-left: 3.5px solid rgb(121, 117, 117);
    margin-left: 9px;
    }
</style>