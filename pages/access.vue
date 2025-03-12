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
        アクセス
      </h1>

      <div class="grid md:grid-cols-2 gap-12">
        <div 
          class="bg-gray-900/90 rounded-2xl p-8 backdrop-blur-sm border border-white/10"
          v-motion
          :initial="{ opacity: 0, x: -50 }"
          :enter="{ opacity: 1, x: 0 }"
        >
          <h2 class="text-2xl font-bold mb-6 font-zen">会場案内</h2>
          <div class="space-y-4 text-white/80">
            <p>〒169-0072</p>
            <p>東京都新宿区大久保３丁目６−１</p>
            <p>海城中学高等学校</p>
          </div>
        </div>

        <div 
          class="bg-gray-900/90 rounded-2xl p-8 backdrop-blur-sm border border-white/10"
          v-motion
          :initial="{ opacity: 0, x: 50 }"
          :enter="{ opacity: 1, x: 0 }"
          :delay="100"
        >
          <h2 class="text-2xl font-bold mb-6 font-zen">交通アクセス</h2>
          <div class="space-y-6">
            <div>
              <h3 class="text-lg font-medium mb-2 text-purple-400">電車でお越しの方</h3>
              <p class="text-white/80">新大久保駅（山手線）徒歩5分</p>
            </div>
            <div>
              <h3 class="text-lg font-medium mb-2 text-purple-400">飛行機でお越しの方</h3>
              <p class="text-white/80">羽田空港　徒歩5時間11分</p>
            </div>
          </div>
        </div>

        <div 
          class="bg-gray-900/90 rounded-2xl p-8 backdrop-blur-sm border border-white/10 md:col-span-2"
          v-motion
          :initial="{ opacity: 0, y: 50 }"
          :enter="{ opacity: 1, y: 0 }"
          :delay="200"
        >
          <h2 class="text-2xl font-bold mb-6 font-zen">注意事項</h2>
          <ul class="list-disc list-inside space-y-2 text-white/80">
            <li>駐車場の用意はございません。公共交通機関をご利用ください。</li>
            <li>校内は全面禁煙となっております。</li>
            <li>貴重品は各自で管理をお願いいたします。</li>
          </ul>
        </div>
      </div>
    </div>
  </main>
</template>