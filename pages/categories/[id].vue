<template>
    <!-- <HomeBanner /> -->
    <div class="relative h-[30rem] overflow-hidden">
        <div class="flex h-full slide" style="width: 500%;">
            <!-- Slide 1 -->
            <div class="w-1/5 h-full bg-cover bg-center relative"
                style="background-image: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.4)), url('/65959e41871a5.jpg');">
                <div class="absolute inset-0 flex items-center justify-center text-center text-white px-4">
                    <div>
                        <h1 class="text-4xl md:text-6xl font-bold mb-4">Attractions</h1>
                        <p class="text-lg md:text-xl mb-8 max-w-3xl">Your Ultimate Inlet Beach Escape — Thoughtfully
                            Curated for
                            Relaxation, Comfort, and Unforgettable Moments by the Sea</p>

                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- Section first -->
    <div class="mt-24 px-4 py-8 lg:py-16">
        <!-- The Gauge Coffeehouse Section -->
        <div class="flex scale-100  justify-center relative items-center">
            <!-- Image Section -->
            <div class="order-2 lg:order-1 ">
                <div class="relative">
                    <img src="/categories/657a2829e5278.png"
                        alt="The Gauge Coffeehouse outdoor seating area with yellow umbrella, rustic blue building, stone patio, and wooden chairs"
                        class="w-full h-full rounded shadow-xl  scale-110">
                </div>
            </div>

            <!-- Content Section -->
            <div
                class="order-1 lg:order-2 relative border border-gray-200 bg-white max-w-2xl scale-100 px-6 py-6 pb-44">
                <!-- Dotted Pattern Background - positioned on the right side -->
                <div class="relative pr-4 lg:pr-8">
                    <h1 class="text-3xl lg:text-3xl  font-bold text-[#1B7895] mb-6 lg:mb-8 leading-tight ">
                        The Gauge Coffeehouse & Humble Pie
                    </h1>
                    <p class="text-gray-700 text-base lg:text-lg leading-relaxed lg:leading-relaxed ">
                        The Gauge Coffeehouse is a casual place to start your day. They offer
                        coffee drinks, homemade bagels and muffins. This is also the Chattooga
                        Whitewater Shop where you'll find river gear, clothing and information about
                        shuttle service to and from the river. Humble Pie Pizza is next door to The
                        Gauge. It's a great place to unwind after a day exploring the area.
                    </p>

                </div>
            </div>
            <div class="absolute right-28 -bottom-14 -z-10">
                <img src="/categories/dot-shape.png" alt="">
            </div>
        </div>
    </div>
    <!-- Section second (reversed layout) -->
    <div class="mt-32 px-4 py-8 lg:py-16">
        <!-- Beach Retreat Section -->
        <div class="flex scale-100 justify-center relative items-center">
            <!-- Content Section (now on the left) -->
            <div class="order-1 z-20 relative border border-gray-200 bg-white max-w-2xl scale-100 px-8 py-6 pb-44">
                <div class="relative pr-4 lg:pr-8">
                    <h1 class="text-3xl lg:text-3xl font-bold text-[#1B7895] mb-6 lg:mb-8 leading-tight ">
                        Coastal Beach Experience
                    </h1>
                    <p class="text-gray-700 text-base lg:text-lg leading-relaxed lg:leading-relaxed ">
                        Experience the pristine coastline at this breathtaking beach destination. With
                        crystal clear waters and white sandy shores, this is the perfect place to relax and
                        unwind. Enjoy swimming, sunbathing, or simply watching the waves roll in. The
                        nearby beachfront restaurants offer fresh seafood and refreshing beverages to
                        complete your perfect beach day experience.
                    </p>
                </div>
            </div>

            <!-- Image Section (now on the right) -->
            <div class="order-2">
                <div class="relative">
                    <img src="/categories/657a2829e5278.png"
                        alt="Beautiful beach scene with crystal clear waters and white sandy shores"
                        class="w-full h-full rounded shadow-xl  scale-100">
                </div>
            </div>

            <!-- Dotted pattern (now on the left side) -->
            <div class="absolute left-28 -bottom-14 -z-10">
                <img src="/categories/dot-shape.png" alt="">
            </div>
        </div>
    </div>
</template>

<script setup>

// Get the route parameter
const route = useRoute();
const categoryId = route.params.id;


</script>
