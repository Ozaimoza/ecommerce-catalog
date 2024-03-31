<script setup>
import sadface from '../assets/sad-face.png'
const props = defineProps({
    
  nextPage: Function
});

</script>

<template>
    <div  class="bg">
        <section class="product"> 
            <div class="img-container">
                <img class="img" :src="sadface" alt="sad face">
                
            </div>
            <div class="btn-group">
                    <p>This product is unavailable to show</p>
                    <button class="btn" @click="nextPage">Next product</button>
            </div>
        </section>
    </div>
</template>

<style scoped>
.bg {
    height: 428px;
    background-color: #DCDCDC;
}

.btn-group {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    z-index: 1; /* Menempatkan btn-group di depan img-container */
}
p{
    text-align: center;
}
.btn{
box-sizing: border-box;
width: 465px;
height: 42px;
background: #FFFFFF;
border: 3px solid #000000;
border-radius: 4px;
font-weight: bold;
font-size: larger;
}

.img-container {
    display: flex;
    justify-content: center;
    overflow: hidden;
    margin: auto;
}

.img {
    object-fit: full;
    max-width: 100%;
    max-height: 100%;
}
</style>
