<script setup>
import image from '../assets/bg-pattern.png'

const props = defineProps({
  productData: Object,
  nextPage: Function
});

const truncateDescription = (text, maxLength = 300) => {
    if (text.length <= maxLength) {
        return text;
    }
    // Gunakan slice untuk memotong teks
    return text.slice(0, maxLength) + '...';
}


</script>

<template>
    <div  :class="productData.category === 'men\'s clothing' ? 'background-man' : 'background-woman'">
        <div class="image-container">
            <img :src="image" alt="background" class="repeating-image">
        </div>
        <section class="product"> <!-- Check both isLoading and productData -->
            <div class="image">    
                <img :src="productData.image" alt="Product Image">
            </div>
            <div class="content">
                <div>
                    <h1 :class="productData.category === 'men\'s clothing' ? 'title-man' : 'title-woman'">{{ productData.title }}</h1>
                    <div class="category">
                        <span>{{ productData.category }}</span> 

                        <div class="rating-group">
                            <div class="rating-text">{{productData.rating.rate}}/5</div>
                            <div v-if="productData.category === 'men\'s clothing'" class="rating-circle">
                                <span v-for="index in 5" :key="index" :class="{ 'circle-man': true, 'checked-man': index <= Math.floor(productData.rating.rate) }"></span>
                            </div>
                            <div v-else class="rating-circle">
                                <span v-for="index in 5" :key="index" :class="{ 'circle-woman': true, 'checked-woman': index <= Math.floor(productData.rating.rate) }"></span>
                            </div>
                        </div>
                    </div>
                    <hr>
                    <div class="description">
                        <p>{{ truncateDescription(productData.description) }}</p>
                    </div>
                </div>
                <div>
                <hr>
                    <h2>${{ productData.price }}</h2>
                    <div class="button-group">
                        <button :class="productData.category === 'men\'s clothing' ? 'button-man1' : 'button-woman1'">Buy now</button>
                        <button @click="nextPage" :class="productData.category === 'men\'s clothing' ? 'button-man2' : 'button-woman2'">Next product</button>
                    </div>
                </div>
            </div>
           
        </section>
</div>
</template>

<style scoped>
.rating-text{
    font-size: larger;
}
.rating-group{
    display: flex;
}
.rating-circle {
  position: relative;
  width: 120px; 
  height: 20px; 
  display: flex;
}

.circle-man {
  width: 18px;
  height: 18px; 
  border-radius: 100%; 
  border-color: #002772;
  border-style: solid;
  border-width: 2px;
  background-color: #ddd; 
  margin-left: 3px;
}

.checked-man {
  background-color: #002772; /* Warna lingkaran berwarna penuh */
}

.circle-woman {
  width: 18px;
  height: 18px; 
  border-radius: 100%; 
  border-color: #720060;
  border-style: solid;
  border-width: 2px;
  background-color: #ddd; 
  margin-left: 3px;
}

.checked-woman {
  background-color: #720060; /* Warna lingkaran berwarna penuh */
}
</style>
