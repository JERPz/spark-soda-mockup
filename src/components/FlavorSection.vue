<script setup>
defineProps(['data'])
</script>

<template>
    <div class="container mx-auto grid grid-cols-1 lg:grid-cols-2 gap-10 items-center w-full">

        <div class="text-center lg:text-left">
            <transition name="fade-slide" mode="out-in">
                <div :key="data.id">
                    <p class="text-sm md:text-lg uppercase tracking-[0.3em] font-bold mb-2 opacity-70">
                        {{ data.tagline }}
                    </p>
                    <h1 class="text-6xl md:text-8xl font-black mb-6 leading-tight uppercase transition-colors duration-500"
                        :style="{ color: data.color }">
                        {{ data.title }}
                    </h1>
                    <p class="text-lg md:text-xl opacity-70 leading-relaxed max-w-xl mx-auto lg:mx-0">
                        {{ data.desc }}
                    </p>

                    <div class="flex justify-center lg:justify-start gap-10 mt-10">
                        <div v-for="(val, label) in data.stats" :key="label" class="text-center">
                            <span class="block text-4xl md:text-5xl font-black transition-colors duration-500"
                                :style="{ color: data.color }">{{ val }}</span>
                            <span class="text-[10px] uppercase tracking-widest opacity-50 font-bold">{{ label }}</span>
                        </div>
                    </div>

                    <button
                        class="mt-12 px-12 py-5 rounded-full font-black text-black text-lg transition-all hover:scale-105 active:scale-95 shadow-2xl cursor-pointer"
                        :style="{ backgroundColor: data.color }">
                        GET THE SPARK
                    </button>
                </div>
            </transition>
        </div>

        <div class="flex justify-center items-center">
            <img :src="data.image" loading="eager" decoding="async"
                class="w-full max-w-[280px] md:max-w-[420px] drop-shadow-[0_40px_60px_rgba(0,0,0,0.9)] animate-float" />
        </div>
    </div>
</template>

<style scoped>
.fade-slide-enter-active,
.fade-slide-leave-active {
    transition: all 0.2s ease-out;
}
</style>