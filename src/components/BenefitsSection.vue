<template>
    <section class="py-32 bg-black relative z-30 shadow-[0_-50px_100px_rgba(0,0,0,0.9)]">
        <div class="container mx-auto px-6">
            <div class="text-center mb-20">
                <h2 class="text-5xl md:text-7xl font-black italic uppercase tracking-tighter mb-4">
                    The <span class="text-spark-green">Spark</span> Difference
                </h2>
                <p class="text-white/40 uppercase tracking-[0.3em]">Pure Power • No Compromise</p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
                <div v-for="item in benefits" :key="item.title"
                    class="p-10 rounded-[2rem] bg-white/[0.03] border border-white/10 hover:border-spark-green/40 transition-all group">
                    <div class="text-5xl mb-6 group-hover:scale-110 transition-transform">{{ item.icon }}</div>
                    <h3 class="text-2xl font-bold mb-3 italic uppercase">{{ item.title }}</h3>
                    <p class="text-white/50 leading-relaxed">{{ item.desc }}</p>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
const benefits = [
    { icon: '⚡', title: 'Energy', desc: 'Natural caffeine for a steady, clean lift.' },
    { icon: '🍃', title: 'Natural', desc: 'No artificial flavors. Just real fruit extracts.' },
    { icon: '🚫', title: 'Zero Sugar', desc: 'Sweetened with Stevia. 0 calories, 100% taste.' },
    { icon: '🧠', title: 'Focus', desc: 'B-Vitamins to keep your mind sharp all day.' }
]
</script>