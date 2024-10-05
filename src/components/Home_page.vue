<template>
    <div class="bg-white min-h-screen">
        <nav class="fixed top-0 left-0 w-full z-50 flex justify-between items-center p-4 bg-white drop-shadow-lg">
            <img src="./logo.jpg" class="w-20" />
            <div class="flex items-center ml-auto space-x-4">
                <form @submit.prevent="handleSearch" class="flex items-center bg-gray-100 rounded-full px-3 py-2">
                    <input v-model="searchQuery" type="text" placeholder="Search..." class="w-full px-3 py-2 rounded-l-full focus:outline-none bg-white text-gray-800 border-none" />
                    <button class="bg-[#590D82] w-8 h-8 flex items-center justify-center text-white rounded-full">
                        <i class="fa-solid fa-magnifying-glass"></i>
                    </button>
                </form>
                <button @click="toggleMenu" class="bg-[#590D82] text-white rounded-full px-4 py-2 hover:bg-[#45076a] transition-all">
                    Menu
                </button>
                <button class="bg-[#590D82] text-white rounded-full px-4 py-2 hover:bg-[#45076a] transition-all">
                    Log In
                </button>
                <button class="bg-[#590D82] text-white rounded-full px-4 py-2 hover:bg-[#45076a] transition-all">
                    Sign Up
                </button>
            </div>
        </nav>
           <!-- header -->
        <header class="relative mt-[100px] w-full h-[350px] bg-cover bg-center" :style="{ backgroundImage: `url(${backgroundImage})` }">
            <div class="absolute inset-0 bg-black bg-opacity-50 flex flex-col justify-center items-center text-white text-center">
                <h1 class="text-4xl font-bold">Welcome to UniConnect</h1>
                <p class="mt-4 text-lg">Connecting students and professionals across Ethiopia</p>
                <button class="bg-[#590D82] text-white rounded-full px-6 py-3 mt-6 hover:bg-[#45076a] transition-all">
                    Get Started
                </button>
            </div>
        </header>

        <main>
            <div class="flex justify-center space-x-10 bg-[#590D82] text-white py-5 mb-5">
                <p>Admission</p>
                <p>Blog</p>
                <p>Research</p>
                <p>Internships</p>
                <p>Scholarships</p>
            </div>
            <section class="text-center mb-10">
                <h2 class="text-2xl font-bold text-slate-900">Latest NEWS</h2>
                <div class="border-t-2 border-slate-900 w-1/4 mx-auto mt-2 mb-8"></div>

                <!-- Swiper Carousel -->
                <Swiper
                    :slides-per-view="3"
                    :space-between="30"
                    :loop="true"
                    :autoplay="{ delay: 3000, disableOnInteraction: false }"
                    navigation
                    pagination
                    class="mx-5"
                    :modules="[Autoplay, Navigation, Pagination]" >
                <SwiperSlide v-for="(news, index) in newsItems" :key="index">
            <div class="relative group">
                <img :src="news.imgUrl" class="w-full h-48 object-cover" />
                <div class="absolute inset-0 bg-black bg-opacity-50 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-300">
                    <span class="text-white text-lg">{{ news.text }}</span>
                </div>
            </div>
        </SwiperSlide>
                </Swiper>
            </section>
        </main>
        <!-- footer -->
        <footer class="bg-gradient-to-r from-purple-800 to-purple-500 text-white py-8">
            <div class="flex justify-center space-x-6 mb-4">
                <a href="#" class="text-xl"><i class="fab fa-facebook"></i></a>
                <a href="#" class="text-xl"><i class="fab fa-twitter"></i></a>
                <a href="#" class="text-xl"><i class="fab fa-instagram"></i></a>
                <a href="#" class="text-xl"><i class="fab fa-linkedin"></i></a>
            </div>
            <div class="text-center text-sm">
                © 2024 UniConnect. All rights reserved.
            </div>
        </footer>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import { Swiper, SwiperSlide } from 'swiper/vue';
import 'swiper/swiper-bundle.css';
import { Autoplay, Navigation, Pagination } from 'swiper/modules';

const isMenuOpen = ref(false);
const searchQuery = ref('');
const backgroundImage = 'https://i.pinimg.com/236x/14/07/29/140729b1f0146860cd7887cce9d925a2.jpg';

const menuItems = ref(['Menu Item 1', 'Menu Item 2', 'Menu Item 3', 'Menu Item 4']);
const newsItems = ref([
    { text: 'Text for Box 1', imgUrl: 'https://i.pinimg.com/236x/62/ea/92/62ea92884a7c7bc08faa546ce6102321.jpg' },
    { text: 'Text for Box 2', imgUrl: 'https://i.pinimg.com/236x/43/97/4c/43974caa8c4f54e970ae55af2069e15e.jpg' },
    { text: 'Text for Box 3', imgUrl: 'https://i.pinimg.com/236x/43/97/4c/43974caa8c4f54e970ae55af2069e15e.jpg' },
    { text: 'Text for Box 4', imgUrl: 'https://i.pinimg.com/236x/43/97/4c/43974caa8c4f54e970ae55af2069e15e.jpg' },
    { text: 'Text for Box 5', imgUrl: 'https://i.pinimg.com/236x/43/97/4c/43974caa8c4f54e970ae55af2069e15e.jpg' },
]);


const handleSearch = () => {
    console.log(searchQuery.value);
};

const toggleMenu = () => {
    isMenuOpen.value = !isMenuOpen.value;
};
</script>

<style scoped>
.swiper-button-next,
.swiper-button-prev {
    color: #590D82;
}

.swiper-pagination-bullet {
    background-color: #590D82;
}

.swiper-pagination-bullet-active {
    background-color: #45076a;
}
</style>
