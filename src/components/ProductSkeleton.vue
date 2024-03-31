<script setup>


</script>

<template>
    <div  class="bg-skeleton">
        <section class="product-skeleton"> <!-- Check both isLoading and productData -->
            <div class="img-skeleton">    
                <!-- <img :src="productData.image" alt="Product Image"> -->
            </div>
            <div class="content-skeleton">
                <div>
                    <div class="title-skeleton"></div>
                    <div class="category-skeleton"></div>

                    <div class="description-skeleton">
                    </div>
                </div>
                <div>

                    <div class="price-skeleton"></div>
                    <div class="btn-group">
                        <div class="btn-skeleton"></div>
                        <div class="btn-skeleton"></div>
                    </div>
                </div>
            </div>
           
        </section>
</div>
</template>

<style scoped>

    @keyframes pulse {
        0% {
            background-color: #94A3B8;
        }

        50% {
            background-color: #CBD5E1;
        }

        100% {
            background-color: #94A3B8;
        }
    }

.bg-skeleton {
    height: 428px;
    background-color: #DCDCDC;
}

.product-skeleton{
    display: flex;
    gap: 5px;
    margin: auto;
    width: 1034px;
    height: 580px;
    background-color: #E2E8F0;
    border-radius: 5px;
    box-shadow: 5px 5px 15px rgba(0, 0, 0, 0.5);

  /* Menengahkan elemen secara horizontal dan vertikal */
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.product-skeleton .img-skeleton{
    height: 80%;
    width: 50%;
    display: flex;
    justify-content: center;
    margin: auto;
    margin-left: 5%;
    animation: pulse 2s infinite ease-in-out;
    
}

.product-skeleton .content-skeleton{
    display: flex;
    justify-content: space-between;
    flex-direction: column;
    width: 100%; 
    max-height: 548px;
    padding: 50px;
}

.title-skeleton{
    animation: pulse 2s infinite ease-in-out;
    height: 55px;
}

.category-skeleton{
    animation: pulse 2s infinite ease-in-out;
    height: 20px;
    margin-top: 10px;
}

.description-skeleton{
    animation: pulse 2s infinite ease-in-out;
    height: 250px;
    margin-top: 10px;
}

.price-skeleton{
    animation: pulse 2s infinite ease-in-out;
    height: 30px;
    width: 100px;
    margin-top: 10px;
}

.btn-group{
    display: flex;
    gap: 10px;
}

.btn-skeleton{
    animation: pulse 2s infinite ease-in-out;
    height: 30px;
    width: 50%;
    margin-top: 10px;
}

</style>
