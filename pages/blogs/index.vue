<template>
    <div class="">
        <!-- <HomeBanner /> -->
        <div class="relative h-[45rem] overflow-hidden">
            <div class="flex h-full slide" style="width: 500%;">
                <!-- Slide 1 -->
                <div class="w-1/5 h-full bg-cover bg-center relative"
                    style="background-image: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.4)), url('/CA_LakeCowichan_CA_Header-1-1.jpg');">
                    <div class="absolute inset-0 flex items-center justify-center text-center text-white px-4">
                        <div>
                            <h1 class="text-4xl md:text-6xl font-bold mb-4">The Latest News and Blog</h1>
                            <p class="text-lg md:text-xl mb-8 max-w-3xl">Your Ultimate Inlet Beach Escape — Thoughtfully
                                Curated for
                                Relaxation, Comfort, and Unforgettable Moments by the Sea</p>

                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="py-8">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8 max-w-7xl mx-auto px-4">
                <article v-for="(blog, index) in blogs" :key="index" :class="[
                    'overflow-hidden group transition-shadow duration-300',
                    index % 2 === 0 ? '' : 'bg-white'
                ]">
                    <div class="relative">
                        <!-- <div class="date-box">
                            <div class="p-3">
                                <div class="text-xs font-semibold text-gray-600 uppercase tracking-wide">{{ blog.month
                                    }}</div>
                                <div class="text-2xl font-bold text-gray-900">{{ blog.day }}</div>
                            </div>
                        </div> -->
                        <img :src="blog.image" :alt="blog.title"
                            class="w-full h-64 sm:h-72 md:h-80 object-cover group-hover:scale-105 transition-transform duration-300" />
                    </div>

                    <div class="py-6">
                        <!-- <div class="flex items-center gap-1 mb-4">
                            <template v-for="(category, i) in blog.categories" :key="i">
                                <span class="text-sm font-semibold textColor uppercase tracking-wider">
                                    {{ category }}
                                </span>
                                <span v-if="i < blog.categories.length - 1" class="text-gray-400">•</span>
                            </template>
                        </div> -->

                        <h2
                            class="text-xl sm:text-2xl font-bold text-gray-900 mb-4 group-hover:text-gray-600 transition-colors duration-300">
                            {{ blog.title }}
                        </h2>

                        <p class="text-gray-600 mb-6 leading-relaxed">
                            {{ blog.excerpt }}
                        </p>

                        <button
                            class="inline-flex items-center gap-2 text-gray-700 font-semibold hover:text-gray-700 transition-colors duration-300 group/btn"
                            @click="navigateTo(`/blogs/${index+1}`)"
                            >
                            <span class="text-sm cool-link uppercase tracking-wider">READ MORE</span>
                            <Icon name="lucide:chevron-right"
                                class="text-lg group-hover/btn:translate-x-1 transition-transform duration-300" />
                        </button>
                    </div>
                </article>
            </div>
        </div>
    </div>
</template>

<script setup>
// Define page metadata
useHead({
    title: 'Lake Articles',
    meta: [
        { name: 'description', content: 'Discover the latest articles about Lake  activities and dining' }
    ]
});

// Blog data array
const blogs = ref([
    {
        month: 'MAR',
        day: '24',
        image: 'https://images.unsplash.com/photo-1544551763-46a013bb70d5?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80',
        categories: ['NEWS', 'WELLNESS'],
        title: 'Top Activities to Enjoy at Lake ',
        excerpt: 'Tucked away in the heart of Vancouver Island, Lake  is more than just a peaceful getaway—its an outdoor playground for adventurers, nature lovers, and ...'
    },
    {
        month: 'MAR',
        day: '12',
        image: 'https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80',
        categories: ['DINING', 'NEWS'],
        title: 'Must-Try Restaurants Around Lake ',
        excerpt: 'When it comes to travel, discovering local flavors is half the experience. Whether youre starting your day with a cozy café breakfast or unwinding after ...'
    },
    {
        month: 'APR',
        day: '05',
        image: 'https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80',

        categories: ['ADVENTURE', 'TRAVEL'],
        title: 'Hiking Trails with Breathtaking Views',
        excerpt: 'Explore the hidden gems of Lake s backcountry with these scenic hiking trails. From beginner-friendly paths to challenging terrain with rewarding vistas...'
    },
    {
        month: 'APR',
        day: '18',
        image: 'https://images.unsplash.com/photo-1517248135467-4c7edcad34c4?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80',
        categories: ['ACCOMMODATION', 'TIPS'],
        title: 'Where to Stay: Lake s Best Properties',
        excerpt: 'From lakefront cabins to luxury retreats, find the perfect place to call home during your Lake  getaway. We have curated a list of properties that offer...'
    },
    {
        month: 'MAY',
        day: '10',
        image: 'https://images.unsplash.com/photo-1506905925346-21bda4d32df4?auto=format&fit=crop&w=1000&q=80',
        categories: ['WILDLIFE', 'PHOTOGRAPHY'],
        title: 'Wildlife Watching: A Photographer is Guide',
        excerpt: 'Lake s diverse ecosystem is home to an impressive array of wildlife. Grab your camera and discover the best spots and times to capture these magnificent...'
    },
    {
        month: 'MAY',
        day: '26',
        image: 'https://images.unsplash.com/photo-1587825140708-dfaf72ae4b04?auto=format&fit=crop&w=1000&q=80',
        categories: ['EVENTS', 'COMMUNITY'],
        title: 'Summer Events Calendar: Whats Happening',
        excerpt: 'As the weather warms up, Lake  comes alive with festivals, markets, and community gatherings. Mark your calendar for these canot-miss events happening...'
    }
]);
</script>

<style scoped>
.date-box {
    position: absolute;
    top: 16px;
    left: 16px;
    background-color: white;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}


.cool-link {
    display: inline-block;
    color: #000;
    text-decoration: none;
}

.cool-link::after {
    content: '';
    display: block;
    width: 0;
    height: 2px;
    background: #000;
    transition: width .3s;
}

.cool-link:hover::after {
    width: 100%;
    transition: width .3s;
}
</style>
