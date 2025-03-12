<template>
  <main class="pt-24 min-h-screen bg-gradient-to-br from-gray-900 via-purple-900/20 to-gray-900">
    <div 
      class="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1492684223066-81342ee5ff30?auto=format&fit=crop&q=80')] bg-cover bg-center opacity-5"
    ></div>
    
    <div class="container mx-auto px-4 py-12 relative">
      <h1 
        class="text-5xl font-bold mb-12 bg-clip-text text-transparent bg-gradient-to-r from-purple-400 to-pink-400 font-zen"
        v-motion
        :initial="{ opacity: 0, y: 50 }"
        :enter="{ opacity: 1, y: 0 }"
      >
        スケジュール
      </h1>

      <div class="grid md:grid-cols-2 gap-12">
        <div 
          v-for="(day, index) in schedule" 
          :key="index"
          class="bg-gray-900/90 rounded-2xl p-8 backdrop-blur-sm border border-white/10"
          v-motion
          :initial="{ opacity: 0, x: index % 2 === 0 ? -50 : 50 }"
          :enter="{ opacity: 1, x: 0 }"
          :delay="index * 200"
        >
          <h2 class="text-2xl font-bold mb-6 font-zen">{{ day.date }}</h2>
          <div class="space-y-4">
            <div 
              v-for="event in day.events" 
              :key="event.time" 
              class="flex p-4"
            >
              <div class="w-24 flex-shrink-0 text-purple-400 font-medium">{{ event.time }}</div>
              <div class="flex-grow">
                <p class="font-medium">{{ event.title }}</p>
                <p v-if="event.description" class="text-sm text-white/60">{{ event.description }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script setup>
const schedule = [
  {
    date: '9月13日（土）',
    events: [
      { time: '8:45', title: '開場' },
      { time: '9:30', title: '展示・模擬店開始' },
      { time: '13:00', title: 'ステージ発表', description: '吹奏楽部演奏、演劇部公演' },
      { time: '16:00', title: '1日目終了' }
    ]
  },
  {
    date: '9月14日（日）',
    events: [
      { time: '8:45', title: '開場' },
      { time: '9:30', title: '展示・模擬店開始' },
      { time: '13:00', title: 'ステージ発表', description: '合唱部発表、軽音楽部ライブ' },
      { time: '15:00', title: '2日目終了'},
      { time: '16:00', title: '後夜祭' }
    ]
  }
];
</script>