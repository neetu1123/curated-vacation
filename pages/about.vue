<template>
  <div>
    <!-- <HomeBanner /> -->
    <div class="relative h-[45rem] overflow-hidden">
      <div class="flex h-full slide" style="width: 500%;">
        <!-- Slide 1 -->
        <div class="w-1/5 h-full bg-cover bg-center relative"
          style="background-image: linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.4)), url('/CA_LakeCowichan_CA_Header-1-1.jpg');">
          <div class="absolute inset-0 flex items-center justify-center text-center text-white px-4">
            <div>
              <h1 class="text-4xl md:text-6xl font-bold mb-4">About Us</h1>
              <p class="text-lg md:text-xl mb-8 max-w-3xl">Your Ultimate Inlet Beach Escape — Thoughtfully Curated for
                Relaxation, Comfort, and Unforgettable Moments by the Sea</p>

            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- First Section - Our Journey -->
    <section class="bg-gradient-to-r from-amber-50 to-[#E9F4F6] py-16 pb-28 px-4 lg:px-8">

      <div class="max-w-7xl mx-auto">
        <div class="grid lg:grid-cols-2 gap-20 items-center">
          <!-- Left Content -->
          <div class="space-y-8">
            <p class="text-base font-semibold lightText uppercase">OUR JOURNEY</p>
            <h1 class="text-xl sm:text-3xl font-bold textColor leading-tight">
              Inspired by Nature, Built for You
            </h1>

            <div class="space-y-6 text-gray-700 text-lg leading-relaxed">
              <p>
                Alisha and Matt have always believed that the best moments in life happen when we slow down and
                reconnect—with nature, with loved ones, and with ourselves. After years of juggling careers, travel, and
                the pace of modern life, they discovered the peaceful charm of Cowichan Lake and knew they had found
                something special.
              </p>

              <p>
                What started as a quiet personal retreat slowly became a vision: a place where others could escape the
                noise, breathe deeply, and enjoy the beauty of simple, meaningful moments. Together, they created
                Cowichan Lake Cottages—a boutique laketown getaway designed for comfort, connection, and a little bit of
                magic.
              </p>

              <p>
                Whether you're looking for a weekend of solitude, a romantic escape, or time with friends and family,
                Alisha and Matt invite you to share in the peace and natural beauty that first inspired them—and to make
                this special place part of your own story.
              </p>
            </div>

            <NuxtLink to="/properties"
              class="inline-block bgGradient hover:bg-[#1B7895] text-white px-8 py-4 font-semibold tracking-wide uppercase transition-colors duration-300 hover:scale-105">
              OUR PROPERTIES
            </NuxtLink>
          </div>

          <!-- Right Image -->
          <div class="relative">
            <div class="aspect-[4/5] rounded overflow-hidden shadow-2xl">
              <img src="/1f61d721-20a2-4cac-b2c1-874dc0124cd0.jpg" alt="Lake View" class="w-full h-full object-cover" />
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
useHead({
  title: 'About Us - A Curated Vacation',
  meta: [
    { name: 'description', content: 'Learn about our journey and what makes our properties special.' }
  ]
})
</script>
<style>
.parallax {
  /* The image used */
  background-image: url("/original.webp");

  /* Create the parallax scrolling effect */
  background-attachment: fixed;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  opacity: 0.9;
  mix-blend-mode: overlay;
}
</style>