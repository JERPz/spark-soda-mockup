<script setup>
defineProps({
    id: String,
    tagline: String,
    title: String,
    desc: String,
    image: String,
    color: String,
    isHero: Boolean,
    stats: Object
})
</script>

<template>
    <section :id="id" class="relative min-h-screen flex items-center px-[8%] py-20 overflow-hidden">
        <div class="container mx-auto grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">

            <div class="z-10 text-center lg:text-left order-2 lg:order-1">
                <p v-if="tagline" class="text-spark-green text-sm md:text-lg uppercase tracking-[0.3em] font-bold mb-4">
                    {{ tagline }}
                </p>
                <h1 class="text-6xl md:text-8xl font-black mb-6 leading-tight uppercase" :style="{ color: color }">
                    {{ title }}
                </h1>
                <p class="text-lg md:text-xl opacity-70 leading-relaxed max-w-xl mx-auto lg:mx-0">
                    {{ desc }}
                </p>

                <div class="flex justify-center lg:justify-start gap-8 md:gap-12 mt-12">
                    <div v-for="(val, label) in stats" :key="label" class="group">
                        <span class="block text-4xl md:text-5xl font-black transition-transform group-hover:scale-110"
                            :style="{ color: color }">
                            {{ val }}
                        </span>
                        <span class="text-[10px] md:text-xs uppercase tracking-widest opacity-50 font-bold">{{ label
                            }}</span>
                    </div>
                </div>

                <button
                    class="mt-12 px-12 py-5 rounded-full font-black text-black text-lg transition-all hover:scale-105 active:scale-95 shadow-xl cursor-pointer"
                    :style="{ backgroundColor: color }">
                    GET THE SPARK
                </button>
            </div>

            <div class="relative flex justify-center items-center order-1 lg:order-2">
                <img :src="image"
                    class="w-full max-w-[280px] md:max-w-[400px] drop-shadow-[0_40px_60px_rgba(0,0,0,0.8)]"
                    :class="{ 'animate-float': isHero }" />
            </div>
        </div>

        <div v-if="isHero" class="absolute bottom-10 left-1/2 -translate-x-1/2 hidden md:block opacity-40">
            <div class="w-7 h-11 border-2 border-white rounded-full flex justify-center p-2">
                <div class="w-1 h-2 bg-white rounded-full animate-bounce"></div>
            </div>
        </div>
    </section>
</template>