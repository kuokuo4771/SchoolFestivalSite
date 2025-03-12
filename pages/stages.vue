<template>
  <main class="pt-24 min-h-screen bg-gradient-to-br from-rose-900/30 via-purple-900/30 to-gray-900">
    <div 
      class="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1516450360452-9312f5e86fc7?auto=format&fit=crop&q=80')] bg-cover bg-center opacity-10"
    ></div>
    
    <div class="container mx-auto px-4 py-12 relative">
      <h1 
        class="text-5xl font-bold mb-12 bg-clip-text text-transparent bg-gradient-to-r from-purple-400 to-pink-400 font-zen"
        v-motion
        :initial="{ opacity: 0, y: 100 }"
        :enter="{ opacity: 1, y: 0 }"
      >
        ステージ発表
      </h1>

      <div class="grid md:grid-cols-2 gap-12">
        <div 
          v-for="(performance, index) in performances" 
          :key="index"
          class="group bg-gray-900/90 rounded-2xl overflow-hidden backdrop-blur-sm transition-all duration-500 hover:bg-purple-900/90 hover:scale-[1.02] hover:shadow-2xl hover:shadow-purple-500/20 border border-white/10"
          v-motion
          :initial="{ opacity: 0, x: index % 2 === 0 ? -50 : 50 }"
          :enter="{ opacity: 1, x: 0 }"
          :delay="index * 100"
        >
          <div class="relative h-48 overflow-hidden">
            <img 
              :src="performance.image" 
              :alt="performance.title"
              class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
            />
            <div class="absolute inset-0 bg-gradient-to-t from-black/80 to-transparent"></div>
            <div class="absolute bottom-0 left-0 right-0 p-6">
              <h2 class="text-2xl font-bold mb-2 font-zen">{{ performance.title }}</h2>
              <div class="flex items-center space-x-2 text-purple-400">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
                  <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm1-12a1 1 0 10-2 0v4a1 1 0 00.293.707l2.828 2.829a1 1 0 101.415-1.415L11 9.586V6z" clip-rule="evenodd" />
                </svg>
                <span class="text-sm">{{ performance.time }}</span>
              </div>
            </div>
          </div>
          
          <div class="p-6">
            <p class="text-white/80 mb-4">{{ performance.description }}</p>
            <div class="space-y-2">
              <h3 class="font-medium text-purple-400 font-zen">演目</h3>
              <ul class="list-disc list-inside text-white/80 space-y-1">
                <li v-for="item in performance.program" :key="item">{{ item }}</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script setup>
const performances = [
  {
    title: '吹奏楽部演奏会',
    time: '9/11 13:00-14:00',
    description: '今年度のコンクール課題曲や、人気アニメ・映画音楽のメドレーなど、バラエティ豊かな演奏をお届けします。',
    image: 'https://images.unsplash.com/photo-1465847899084-d164df4dedc6?auto=format&fit=crop&q=80',
    program: [
      'コンクール課題曲より',
      'ジブリメドレー',
      'ディズニーメドレー',
      'オリジナル組曲「青春の輝き」'
    ]
  },
  {
    title: '演劇部公演',
    time: '9/11 14:30-15:30',
    description: 'オリジナル脚本「時を越えて」を上演。現代と過去を行き来する少女の心温まる物語です。',
    image: 'https://images.unsplash.com/photo-1507676184212-d03ab07a01bf?auto=format&fit=crop&q=80',
    program: [
      '第一幕「出会い」',
      '第二幕「選択」',
      '第三幕「約束」',
      'エピローグ'
    ]
  },
  {
    title: '合唱部発表',
    time: '9/12 13:00-14:00',
    description: '最近のJ-POPから感動する合唱曲まで、多彩なジャンルの合唱パフォーマンスをお届けします。',
    image: 'https://images.unsplash.com/photo-1508700115892-45ecd05ae2ad?auto=format&fit=crop&q=80',
    program: [
      'オープニング「RISE」',
      'ヒップホップメドレー',
      'コンテンポラリー「光と影」',
      'フィナーレ「UNITY」'
    ]
  },
  {
    title: '軽音楽部ライブ',
    time: '9/12 14:30-15:30',
    description: '部内バンドによるライブパフォーマンス。オリジナル曲とカバー曲を織り交ぜてお送りします。',
    image: 'https://images.unsplash.com/photo-1516450360452-9312f5e86fc7?auto=format&fit=crop&q=80',
    program: [
      'バンド1「The Dreamers」',
      'バンド2「Blue Sky」',
      'バンド3「Sunset Drive」',
      'オールメンバーズセッション'
    ]
  }
];
</script>