<template>
  <main
    class="pt-24 min-h-screen bg-gradient-to-br from-indigo-900 via-purple-900/30 to-gray-900"
    :class="{ 'overflow-hidden': selectedExhibition }"
  >
    <div
      class="absolute inset-0 bg-[url('https://images.unsplash.com/photo-1513364776144-60967b0f800f?auto=format&fit=crop&q=80')] bg-cover bg-center opacity-10"
    ></div>

    <div class="container mx-auto px-4 py-12 relative">
      <h1
        class="text-5xl font-bold mb-12 bg-clip-text text-transparent bg-gradient-to-r from-purple-400 to-pink-400 font-zen"
        v-motion
        :initial="{ opacity: 0, y: 100 }"
        :enter="{ opacity: 1, y: 0 }"
        :delay="200"
      >
        展示・作品
      </h1>

      <div class="grid md:grid-cols-2 gap-12">
        <div
          v-for="(exhibition, index) in exhibitions"
          :key="index"
          class="group bg-gray-900/90 rounded-2xl overflow-hidden backdrop-blur-sm transition-all duration-500 hover:bg-purple-900/90 hover:scale-[1.02] hover:shadow-2xl hover:shadow-purple-500/20 cursor-pointer border border-white/10"
          v-motion
          :initial="{ opacity: 0, x: index % 2 === 0 ? -50 : 50 }"
          :enter="{ opacity: 1, x: 0 }"
          :delay="index * 100"
          @click="openModal(exhibition)"
        >
          <div class="relative h-48 overflow-hidden">
            <img
              :src="exhibition.image"
              :alt="exhibition.title"
              class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
            />
            <div
              class="absolute inset-0 bg-gradient-to-t from-black/80 to-transparent"
            ></div>
            <div class="absolute bottom-0 left-0 right-0 p-6">
              <h2 class="text-2xl font-bold mb-2 font-zen">
                {{ exhibition.title }}
              </h2>
              <div class="flex items-center space-x-2 text-purple-400">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-5 w-5"
                  viewBox="0 0 20 20"
                  fill="currentColor"
                >
                  <path
                    fill-rule="evenodd"
                    d="M5.05 4.05a7 7 0 119.9 9.9L10 18.9l-4.95-4.95a7 7 0 010-9.9zM10 11a2 2 0 100-4 2 2 0 000 4z"
                    clip-rule="evenodd"
                  />
                </svg>
                <span class="text-sm">{{ exhibition.location }}</span>
              </div>
            </div>
          </div>

          <div class="p-6">
            <p class="text-white/80 mb-4 leading-relaxed">
              {{ exhibition.description }}
            </p>
            <div class="flex items-center justify-between text-sm">
              <div class="flex items-center space-x-2 text-purple-400">
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="h-5 w-5"
                  viewBox="0 0 20 20"
                  fill="currentColor"
                >
                  <path
                    fill-rule="evenodd"
                    d="M10 18a8 8 0 100-16 8 8 0 000 16zm1-12a1 1 0 10-2 0v4a1 1 0 00.293.707l2.828 2.829a1 1 0 101.415-1.415L11 9.586V6z"
                    clip-rule="evenodd"
                  />
                </svg>
                <span>{{ exhibition.time }}</span>
              </div>
              <div
                class="px-4 py-2 rounded-full bg-purple-500/20 text-purple-400"
              >
                詳細を見る
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Modal -->
    <Transition name="modal">
      <div
        v-if="selectedExhibition"
        class="fixed inset-0 z-50 flex items-center justify-center px-4"
      >
        <div
          class="fixed inset-0 bg-black/60 backdrop-blur-sm"
          @click="closeModal"
        ></div>
        <div
          class="relative bg-gray-900/90 w-full max-w-2xl rounded-2xl overflow-y-auto max-h-[90vh] backdrop-blur-md border border-white/10"
          v-motion
          :initial="{ opacity: 0, scale: 0.9 }"
          :enter="{ opacity: 1, scale: 1 }"
        >
          <div class="overflow-y-auto">
            <img
              :src="selectedExhibition.image"
              :alt="selectedExhibition.title"
              class="w-full object-cover"
            />
            <div class="p-8">
              <h2 class="text-3xl font-bold mb-4 font-zen">
                {{ selectedExhibition.title }}
              </h2>

              <div class="grid grid-cols-2 gap-4 mb-6">
                <div class="flex items-center space-x-2 text-purple-400">
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    class="h-5 w-5"
                    viewBox="0 0 20 20"
                    fill="currentColor"
                  >
                    <path
                      fill-rule="evenodd"
                      d="M5.05 4.05a7 7 0 119.9 9.9L10 18.9l-4.95-4.95a7 7 0 010-9.9zM10 11a2 2 0 100-4 2 2 0 000 4z"
                      clip-rule="evenodd"
                    />
                  </svg>
                  <span>{{ selectedExhibition.location }}</span>
                </div>
                <div class="flex items-center space-x-2 text-purple-400">
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    class="h-5 w-5"
                    viewBox="0 0 20 20"
                    fill="currentColor"
                  >
                    <path
                      fill-rule="evenodd"
                      d="M10 18a8 8 0 100-16 8 8 0 000 16zm1-12a1 1 0 10-2 0v4a1 1 0 00.293.707l2.828 2.829a1 1 0 101.415-1.415L11 9.586V6z"
                      clip-rule="evenodd"
                    />
                  </svg>
                  <span>{{ selectedExhibition.time }}</span>
                </div>
              </div>

              <p class="text-white/80 mb-6">
                {{ selectedExhibition.description }}
              </p>
              <div class="space-y-4">
                <h3 class="text-xl font-semibold font-zen">見どころ</h3>
                <ul class="list-disc list-inside space-y-2 text-white/80">
                  <li
                    v-for="highlight in selectedExhibition.highlights"
                    :key="highlight"
                  >
                    {{ highlight }}
                  </li>
                </ul>
              </div>

              <button
                @click="closeModal"
                class="mt-8 w-full py-3 rounded-lg bg-white/20 hover:bg-white/30 text-white transition-colors"
              >
                閉じる
              </button>
            </div>
          </div>
        </div>
      </div>
    </Transition>
  </main>
</template>

<script setup>
const selectedExhibition = ref(null);

const openModal = (exhibition) => {
  selectedExhibition.value = exhibition;
  document.body.style.overflow = 'hidden';
};

const closeModal = () => {
  selectedExhibition.value = null;
  document.body.style.overflow = '';
};

onUnmounted(() => {
  document.body.style.overflow = '';
});

const exhibitions = [
  {
    title: '美術部展示',
    description:
      '今年のテーマ「未来への扉」をもとに制作した絵画、彫刻作品を展示します。部員たちの想像力と創造性が詰まった空間で、アートの新しい可能性を体験してください。',
    location: '美術室',
    time: '両日 09:00-15:00',
    image:
      'https://images.unsplash.com/photo-1513364776144-60967b0f800f?auto=format&fit=crop&q=80',
    highlights: [
      '大型壁画「未来都市」- 部員全員で制作した圧巻の作品',
      '個人制作コーナー - 各部員の個性が光る多彩な作品群',
      '七宝焼体験 - 簡単な創作体験ができるコーナー',
    ],
  },
  {
    title: '物理部展示',
    description:
      '面白い創作物を展示。来場者も参加できるクレーンゲームもあります。物理の不思議さと楽しさを、この展示を通じて体感していただけます。',
    location: '物理実験室',
    time: '両日 09:00-15:00',
    image:
      'https://images.unsplash.com/photo-1532094349884-543bc11b234d?auto=format&fit=crop&q=80',
    highlights: [
      '物理実験ショー - 毎時00分より実施',
      'クレーンゲームコーナー - 自作クレーンゲームをやってみよう',
      'ゲーム制作物展示 - 部員が制作したゲームを展示',
      'プログラミング体験 - 簡単なロボット制御にチャレンジ',
    ],
  },
  {
    title: '数学部展示',
    description:
      '部誌や毎年大人気の中学受験の算数の予想問題集、解けたら景品がもらえる問題も掲示してあります。',
    location: '合同教室23',
    time: '両日 9:00-15:00',
    image:
      'https://images.unsplash.com/photo-1515281239448-2abe329fe5e5?auto=format&fit=crop&q=80',
    highlights: [
      '白板問題 - 解けたら景品がもらえる！',
      '数学部誌配布 - 部員たちが心を込めて書きました',
      '予想問題配布 - 部員のお手製予想問題集！',
    ],
  },
  {
    title: '写真部展示',
    description:
      '部員たちの様々な写真展示。今年は特別に夜景写真コーナーも設置。部員たちが捉えた感動の瞬間をお楽しみください。',
    location: '視聴覚室',
    time: '両日 9:00-16:00',
    image:
      'https://images.unsplash.com/photo-1452587925148-ce544e77e70d?auto=format&fit=crop&q=80',
    highlights: [
      'くじ引き - 当たると景品がもらえる！',
      '夜景写真特集 - 街の光が織りなす幻想的な世界',
      '部員の作品展 - 部員が心を込めて撮った写真集',
    ],
  },
];
</script>

<style>
.modal-enter-active,
.modal-leave-active {
  transition: all 0.3s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
  transform: scale(0.9);
}

.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>
