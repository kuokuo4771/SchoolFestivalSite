<template>
  <main class="pt-24 min-h-screen bg-gradient-to-br from-amber-900/30 via-purple-900/30 to-gray-900">
    <div 
      class="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1504674900247-0877df9cc836?auto=format&fit=crop&q=80')] bg-cover bg-center opacity-10"
    ></div>
    
    <div class="container mx-auto px-4 py-12 relative">
      <h1 
        class="text-5xl font-bold mb-12 bg-clip-text text-transparent bg-gradient-to-r from-purple-400 to-pink-400 font-zen"
        v-motion
        :initial="{ opacity: 0, y: 100 }"
        :enter="{ opacity: 1, y: 0 }"
      >
        模擬店
      </h1>

      <div class="grid md:grid-cols-3 gap-8">
        <div 
          v-for="(shop, index) in shops" 
          :key="index"
          class="group bg-gray-900/90 rounded-2xl overflow-hidden backdrop-blur-sm transition-all duration-500 hover:bg-purple-900/90 hover:scale-[1.02] hover:shadow-2xl hover:shadow-purple-500/20 border border-white/10"
          v-motion
          :initial="{ opacity: 0, y: 50 }"
          :enter="{ opacity: 1, y: 0 }"
          :delay="index * 100"
        >
          <div class="relative h-48 overflow-hidden">
            <img 
              :src="shop.image" 
              :alt="shop.name"
              class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
            />
            <div class="absolute inset-0 bg-gradient-to-t from-black/80 to-transparent"></div>
            <div class="absolute bottom-0 left-0 right-0 p-6">
              <h2 class="text-2xl font-bold mb-2 font-zen">{{ shop.name }}</h2>
              <div class="flex items-center space-x-2 text-purple-400">
                <span class="text-sm">{{ shop.class }}</span>
              </div>
            </div>
          </div>
          
          <div class="p-6">
            <p class="text-white/80 mb-4">{{ shop.description }}</p>
            <div class="space-y-4">
              <div>
                <h3 class="font-medium text-purple-400 mb-2 font-zen">メニュー</h3>
                <ul class="space-y-2">
                  <li v-for="item in shop.menu" :key="item.name" class="flex justify-between text-white/80">
                    <span>{{ item.name }}</span>
                    <span>{{ item.price }}円</span>
                  </li>
                </ul>
              </div>
              <div class="pt-4 border-t border-white/10">
                <div class="flex items-center space-x-2 text-purple-400">
                  <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                    <path fill-rule="evenodd" d="M5.05 4.05a7 7 0 119.9 9.9L10 18.9l-4.95-4.95a7 7 0 010-9.9zM10 11a2 2 0 100-4 2 2 0 000 4z" clip-rule="evenodd" />
                  </svg>
                  <span>{{ shop.location }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script setup>
const shops = [
  {
    name: 'サーティーワン',
    description: 'たくさんの種類のアイス！',
    image: 'https://images.unsplash.com/photo-1511689660979-10d2b1aada49?auto=format&fit=crop&q=80',
    location: '2号館7階',
    menu: [
      { name: 'チョコアイス', price: 300 },
      { name: 'バニラアイス', price: 350 },
      { name: 'ミントアイス', price: 350 }
    ]
  },
  {
    name: 'クレープ',
    description: '甘いものから,おかず系まで、バリエーション豊かなクレープをご用意。特製ソースとホイップクリームが決め手です。',
    image: 'https://images.unsplash.com/photo-1519676867240-f03562e64548?auto=format&fit=crop&q=80',
    location: '2号館 8階',
    menu: [
      { name: 'チョコバナナ', price: 400 },
      { name: 'いちごホイップ', price: 400 },
      { name: 'ハムチーズ', price: 450 }
    ]
  },
  {
    name: 'フライドポテト',
    description: 'カリッと揚がった熱々ポテト。お好みのフレーバーパウダーでカスタマイズできます。',
    image: 'https://images.unsplash.com/photo-1573080496219-bb080dd4f877?auto=format&fit=crop&q=80',
    location: '前庭理科館前',
    menu: [
      { name: 'レギュラー', price: 300 },
      { name: 'ラージ', price: 400 },
      { name: 'フレーバーパウダー追加', price: 50 }
    ]
  },
  {
    name: 'かき氷屋',
    description: 'ふわふわの氷に特製シロップをかけた本格かき氷。暑い日にぴったりの清涼感をお届けします。',
    image: 'https://images.unsplash.com/photo-1513558161293-cdaf765ed2fd?auto=format&fit=crop&q=80',
    location: '小教室2',
    menu: [
      { name: 'いちご', price: 300 },
      { name: 'ブルーハワイ', price: 300 },
      { name: '抹茶ミルク', price: 350 }
    ]
  },
  {
    name: 'カフェテリア',
    description: 'カフェテリアを解放中です。カレーなどを学校の食堂で食べられます。',
    image: 'https://images.unsplash.com/photo-1546173159-315724a31696?auto=format&fit=crop&q=80',
    location: '4号館近く',
    menu: [
      { name: 'カレー', price: 400 },
      { name: 'うどん', price: 450 },
      { name: 'ラーメン', price: 500 }
    ]
  },
  {
    name: '自動販売機',
    description: '自販機を完備。美味しい飲み物をいつでも。',
    image: 'https://images.unsplash.com/photo-1546173159-315724a31696?auto=format&fit=crop&q=80',
    location: '1,4号館下',
    menu: [
      { name: 'オレンジジュース', price: 100 },
      { name: 'カルピス', price: 120 },
      { name: 'トロピカルジュース', price: 100 }
    ]
  }
];
</script>