<script setup>
import ProductCard from '../components/ProductCard.vue';
import UnavailableCard from '../components/UnavailableCard.vue'
import ProductSkeleton from '../components/ProductSkeleton.vue';
import { ref } from 'vue';
import axios from 'axios';


// Define a reactive variable to track loading state
let data = ref(null);
let length = ref(null);

const fetchData = async()=>{
    try {
        const response = await axios.get(`https://fakestoreapi.com/products/`);
        length.value = response.data.length
        // console.log(typeof(response.data.length))
    } catch (error) {
        console.error('Error fetching data:', error);
    }
}
fetchData();

const fetchDataById = async (page) => {
    try {
        const response = await axios.get(`https://fakestoreapi.com/products/${page}`);
        data.value = response.data;
        
        // console.log(data)
    } catch (error) {
        console.error('Error fetching data:', error);
    }
}


// page
let page = 1
const nextPage = async() => {
    if (page === length.value){
        page = 1
    } else{
        page++
        // console.log(page)
    }
    data.value = null;
    fetchDataById(page); // Fetch new data for the next product
}

fetchDataById(page);

</script>

<template>
    <div v-if="!data"><ProductSkeleton /></div>
    <div v-else-if="data.category === 'men\'s clothing' || data.category === 'women\'s clothing'">
        <ProductCard :productData="data" :nextPage="nextPage" />
    </div>
    <div v-else>
        <UnavailableCard :nextPage="nextPage" />
    </div>
    
    
</template>

<style scoped>
  /* CSS styles specific to Home component */
</style>