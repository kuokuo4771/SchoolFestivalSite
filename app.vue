<template>
  <div class="min-h-screen bg-gradient-to-br from-gray-900 via-purple-900/20 to-gray-900 text-white font-noto">
    <!-- Navigation -->
    <nav class="fixed w-full z-50 bg-gray-900/80 backdrop-blur-sm border-b border-white/10">
      <div class="container mx-auto px-4 py-4">
        <div class="flex items-center justify-between">
          <NuxtLink 
            to="/" 
            class="text-2xl font-bold tracking-wider font-zen"
            v-motion
            :initial="{ opacity: 0, x: -20 }"
            :enter="{ opacity: 1, x: 0 }"
          >海城文化祭2025</NuxtLink>

          <!-- Share Button -->
          <button 
            @click="isShareOpen = !isShareOpen"
            class="md:ml-auto md:mr-8 relative p-2 hover:text-purple-400 transition-colors"
          >
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8.684 13.342C8.886 12.938 9 12.482 9 12c0-.482-.114-.938-.316-1.342m0 2.684a3 3 0 110-2.684m0 2.684l6.632 3.316m-6.632-6l6.632-3.316m0 0a3 3 0 105.367-2.684 3 3 0 00-5.367 2.684zm0 9.316a3 3 0 105.368 2.684 3 3 0 00-5.368-2.684z" />
            </svg>

            <!-- Share Menu -->
            <div 
              v-if="isShareOpen"
              class="absolute right-0 mt-2 w-48 rounded-lg bg-gray-900/95 shadow-lg py-2 border border-white/10 backdrop-blur-sm z-[60]"
              v-onClickOutside="() => isShareOpen = false"
            >
              <a 
                v-for="(link, index) in shareLinks" 
                :key="index"
                :href="link.url"
                target="_blank"
                class="block px-4 py-2 hover:bg-purple-500/50 transition-colors text-sm text-white"
              >
                {{ link.name }}
              </a>
            </div>
          </button>

          <!-- Hamburger Menu Button -->
          <button 
            @click="isMenuOpen = !isMenuOpen"
            class="p-2 hover:text-purple-400 transition-colors"
          >
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path v-if="!isMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
              <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>
      </div>

      <!-- Mobile Navigation Menu -->
      <Transition name="slide-fade">
        <div v-if="isMenuOpen" class="absolute top-full left-0 right-0">
          <div class="relative">
            <!-- Background with gradient and blur -->
            <div class="absolute inset-0 bg-gray-900/95 backdrop-blur-md border-b border-white/10"></div>
            
            <!-- Background pattern -->
            <div 
              class="absolute inset-0"
              style="background: radial-gradient(circle at 50% 50%, rgba(168, 85, 247, 0.1) 0%, transparent 50%)"
            ></div>

            <!-- Menu content -->
            <div class="container mx-auto py-4 px-4 relative">
              <div class="flex flex-col space-y-4">
                <NuxtLink 
                  v-for="(link, index) in navLinks" 
                  :key="link.path"
                  :to="link.path" 
                  class="hover:bg-white/80 hover:text-gray-900 transition-all py-2 px-4 rounded-lg"
                  @click="isMenuOpen = false"
                  v-motion
                  :initial="{ opacity: 0, x: 20 }"
                  :enter="{ opacity: 1, x: 0 }"
                  :delay="index * 100"
                >
                  {{ link.text }}
                </NuxtLink>
              </div>
            </div>
          </div>
        </div>
      </Transition>
    </nav>

    <!-- Main Content -->
    <NuxtPage />

    <!-- Footer -->
    <footer class="bg-black py-8">
      <div 
        class="container mx-auto px-4 text-center text-white/60"
        v-motion
        :initial="{ opacity: 0, y: 20 }"
        :enter="{ opacity: 1, y: 0 }"
      >
        <p>© 2025 　第134回海城文化祭実行委員会</p>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { onClickOutside } from '@vueuse/core';

const isMenuOpen = ref(false);
const isShareOpen = ref(false);

const navLinks = [
  { text: '展示・作品', path: '/exhibitions' },
  { text: 'ステージ発表', path: '/stages' },
  { text: '模擬店', path: '/shops' },
  { text: 'スケジュール', path: '/schedule' },
  { text: 'アクセス', path: '/access' }
];

const shareLinks = [
  { name: 'Twitter でシェア', url: `https://twitter.com/intent/tweet?text=${encodeURIComponent('第134回海城文化祭、とても面白いよ！ 2025.9.11-9.12')}&url=${encodeURIComponent(window?.location.href)}` },
  { name: 'Facebook でシェア', url: `https://www.facebook.com/sharer/sharer.php?u=${encodeURIComponent(window?.location.href)}` },
  { name: 'LINE で送る', url: `https://line.me/R/msg/text/?${encodeURIComponent('第134回海城文化祭、ぜひ参加してみて！\n' + window?.location.href)}` }
];
</script>

<style>
.page-enter-active,
.page-leave-active {
  transition: all 0.5s;
}
.page-enter-from,
.page-leave-to {
  opacity: 0;
  filter: blur(1rem);
  transform: translateY(20px);
}

.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.3s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateY(-20px);
  opacity: 0;
}
</style>