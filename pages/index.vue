<template>
  <main>
    <!-- Hero Section -->
    <section class="h-screen relative overflow-hidden">
      <div class="absolute inset-0 bg-gradient-to-br from-purple-900/30 via-gray-900/50 to-gray-900"></div>
      <div 
        class="absolute inset-0"
        style="background: radial-gradient(circle at 50% 50%, rgba(168, 85, 247, 0.15) 0%, transparent 70%)"
      ></div>
      <div class="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1492684223066-81342ee5ff30?auto=format&fit=crop&q=80')] bg-cover bg-center opacity-10"></div>
      
      <div class="relative h-full flex items-center justify-center">
        <div class="text-center px-4">
          <h1 
            class="text-7xl md:text-8xl font-bold mb-6 bg-clip-text text-transparent bg-gradient-to-r from-purple-400 to-pink-400 font-zen"
            v-motion
            :initial="{ opacity: 0, y: 100, scale: 0.5 }"
            :enter="{ opacity: 1, y: 0, scale: 1 }"
            :transition="{ type: 'spring', stiffness: 100, damping: 15 }"
          >
            澪
          </h1>
          <p 
            class="text-2xl md:text-3xl mb-8 text-white/90 font-zen"
            v-motion
            :initial="{ opacity: 0 }"
            :enter="{ opacity: 1 }"
            :delay="500"
          >第134回海城文化祭</p>
          <p 
            class="max-w-2xl mx-auto text-lg text-white/80 leading-relaxed"
            v-motion
            :initial="{ opacity: 0, y: 50 }"
            :enter="{ opacity: 1, y: 0 }"
            :delay="700"
          >
            2025.09.13-09.14<br>
            創造性と情熱が交差する2日間。
          </p>
        </div>
      </div>
    </section>

    <!-- Features Grid -->
    <section class="py-24 bg-gradient-to-b from-gray-900 to-gray-900/50 backdrop-blur-sm">
      <div class="container mx-auto px-4">
        <div class="grid md:grid-cols-3 gap-8">
          <NuxtLink 
            to="/exhibitions"
            class="group relative overflow-hidden rounded-2xl aspect-square cursor-pointer"
            v-motion
            :initial="{ opacity: 0, scale: 0.8 }"
            :enter="{ opacity: 1, scale: 1 }"
            :transition="{ type: 'spring', stiffness: 100 }"
          >
            <div class="absolute inset-0 bg-gradient-to-br from-purple-900/50 to-black/50 group-hover:opacity-75 transition-opacity"></div>
            <img src="https://images.unsplash.com/photo-1513364776144-60967b0f800f?auto=format&fit=crop&q=80" alt="展示・作品" class="w-full h-full object-cover transform transition-transform duration-700 group-hover:scale-110">
            <div class="absolute inset-0 p-8 flex flex-col justify-end transform transition-transform duration-500 group-hover:-translate-y-2">
              <h3 class="text-2xl font-bold mb-2 font-zen">展示・作品</h3>
              <p class="text-white/80">美術、科学、文学。多彩な分野の作品展示</p>
            </div>
          </NuxtLink>

          <NuxtLink 
            to="/stages"
            class="group relative overflow-hidden rounded-2xl aspect-square cursor-pointer"
            v-motion
            :initial="{ opacity: 0, scale: 0.8 }"
            :enter="{ opacity: 1, scale: 1 }"
            :delay="100"
            :transition="{ type: 'spring', stiffness: 100 }"
          >
            <div class="absolute inset-0 bg-gradient-to-br from-purple-900/50 to-black/50 group-hover:opacity-75 transition-opacity"></div>
            <img src="https://images.unsplash.com/photo-1516450360452-9312f5e86fc7?auto=format&fit=crop&q=80" alt="ステージ発表" class="w-full h-full object-cover transform transition-transform duration-700 group-hover:scale-110">
            <div class="absolute inset-0 p-8 flex flex-col justify-end transform transition-transform duration-500 group-hover:-translate-y-2">
              <h3 class="text-2xl font-bold mb-2 font-zen">ステージ発表</h3>
              <p class="text-white/80">音楽、演劇、クイズ番組。情熱あふれるパフォーマンス</p>
            </div>
          </NuxtLink>

          <NuxtLink 
            to="/shops"
            class="group relative overflow-hidden rounded-2xl aspect-square cursor-pointer"
            v-motion
            :initial="{ opacity: 0, scale: 0.8 }"
            :enter="{ opacity: 1, scale: 1 }"
            :delay="200"
            :transition="{ type: 'spring', stiffness: 100 }"
          >
            <div class="absolute inset-0 bg-gradient-to-br from-purple-900/50 to-black/50 group-hover:opacity-75 transition-opacity"></div>
            <img src="https://images.unsplash.com/photo-1504674900247-0877df9cc836?auto=format&fit=crop&q=80" alt="模擬店" class="w-full h-full object-cover transform transition-transform duration-700 group-hover:scale-110">
            <div class="absolute inset-0 p-8 flex flex-col justify-end transform transition-transform duration-500 group-hover:-translate-y-2">
              <h3 class="text-2xl font-bold mb-2 font-zen">模擬店</h3>
              <p class="text-white/80">美味しい食べ物の数々</p>
            </div>
          </NuxtLink>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup>
</script>