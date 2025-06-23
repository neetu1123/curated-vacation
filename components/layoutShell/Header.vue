<template>
    <!-- Navigation Bar -->
    <nav class="bg-white  shadow-md fixed w-full top-0 z-40">
        <div class="container mx-auto">
            <div class="flex  items-center h-24">
                <!-- Logo -->
                <div class="flex items-center">
                    <NuxtLink to="/">
                        <h1 class="">
                            <img src="/A Curated Vacation logo_page-0001.jpg" class="h-20" alt="">
                        </h1>
                    </NuxtLink>
                </div>
                <div class="flex-1 flex justify-end items-center">

                    <!-- Desktop Navigation -->
                    <div class="hidden md:flex items-center space-x-8">
                        <button
                            class="bg-[#1B7895] hover:bg-[#5790a1] hover:scale-110 duration-300 text-white px-6 py-2 rounded-full font-medium transition-colors">
                            Book
                        </button>
                        <NuxtLink to="/" class="textColor hover:text-lightText font-medium transition-colors" :class="useRoute().fullPath === '/' && 'underline'" >Home
                        </NuxtLink>
                        <NuxtLink to="/about" class="textColor hover:text-lightText font-medium transition-colors" :class="useRoute().fullPath === '/about' && 'underline'" >About Us
                        </NuxtLink>
                        <NuxtLink to="/property-details" class="textColor hover:text-lightText font-medium transition-colors" :class="useRoute().fullPath === '/property-details' && 'underline'">Property</NuxtLink>
                        <NuxtLink href="/" class="textColor hover:text-lightText font-medium transition-colors" :class="useRoute().fullPath === '/blogs' && 'underline'">Reviews</NuxtLink>
                        <NuxtLink to="/categories"
                            class="textColor hover:text-lightText font-medium transition-colors" :class="useRoute().fullPath === '/categories' && 'underline'">Attractions</NuxtLink>
                        <NuxtLink to="/booking-faqs" class="textColor hover:text-lightText font-medium transition-colors" :class="useRoute().fullPath === '/booking-faqs' && 'underline'">FAQ</NuxtLink>
                        <NuxtLink to="/blogs" class="textColor hover:text-lightText font-medium transition-colors" :class="useRoute().fullPath === '/blogs' && 'underline'">Blogs</NuxtLink>
                        <Nuxtlink to="/contact-us" class="textColor hover:text-lightText font-medium transition-colors" :class="useRoute().fullPath === '/contact-us' && 'underline'">Contact</NuxtLink>
                    </div>

                    <!-- Social Icons -->
                    <div class="hidden md:flex items-center space-x-4 ml-12">
                        <a href="#" class="textColor hover:text-lightText transition-colors">
                            <Icon name="lucide:facebook" width="20" class="!size-5" height="20" />
                        </a>
                        <a href="#" class="textColor hover:text-lightText transition-colors">
                            <Icon name="lucide:instagram" width="20" class="!size-5" height="20" />
                        </a>
                        <a href="#" class="textColor hover:text-lightText transition-colors">
                            <img src="/tik-tok.png" alt="" class="w-5 h-5">
                        </a>

                    </div>
                </div>

                <!-- Mobile Menu Button -->
                <div class="md:hidden">
                    <button @click="toggleMobileMenu" class="text-white hover:text-lightText transition-colors">
                        <Icon name="lucide:menu" width="24" height="24" />
                    </button>
                </div>
            </div>

            <!-- Mobile Menu -->
            <div v-show="mobileMenuOpen" class="md:hidden pb-4">
                <div class="flex flex-col space-y-2">
                    <button
                        class="bg-gradient-to to-lightText from-textColor hover:bg-[#1B7895] text-white px-4 py-2 rounded-full font-medium transition-colors text-center">
                        Book
                    </button>
                    <a href="#"
                        class="text-gray-700 hover:text-orange-500 font-medium py-2 transition-colors">Location</a>
                    <a href="#"
                        class="text-gray-700 hover:text-orange-500 font-medium py-2 transition-colors">Photos</a>
                    <a href="#" class="text-gray-700 hover:text-orange-500 font-medium py-2 transition-colors">Rates</a>
                    <a href="#"
                        class="text-gray-700 hover:text-orange-500 font-medium py-2 transition-colors">Availability</a>
                    <a href="#"
                        class="text-gray-700 hover:text-orange-500 font-medium py-2 transition-colors">Reviews</a>
                </div>
            </div>
        </div>
    </nav>
</template>

<script setup lang="ts">
const mobileMenuOpen = ref(false)

function toggleMobileMenu() {
    mobileMenuOpen.value = !mobileMenuOpen.value;
}

</script>
