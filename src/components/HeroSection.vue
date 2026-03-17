<script setup>
import { onMounted } from 'vue'
import orangeCan from "../assets/orange.png"
import berryCan from "../assets/berry.png"
import limeCan from "../assets/lime.png"

const scrollToFlavors = () => {
    document.getElementById('flavor')?.scrollIntoView({ behavior: 'smooth' })
}
</script>

<template>
    <section class="relative h-screen flex flex-col items-center justify-center text-center px-4 bg-black overflow-hidden z-30">
        <div class="absolute inset-0 flex items-center justify-center pointer-events-none select-none">
            <h1 class="text-[22vw] font-black leading-none tracking-tighter text-white/[0.03] italic uppercase">
                SPARK
            </h1>
        </div>

        <div class="relative z-10 flex flex-col items-center w-full">
            <p class="text-spark-green tracking-[0.4em] font-bold mb-6 uppercase text-xs md:text-sm animate-pulse">
                Pure Energy • Zero Sugar • All Natural
            </p>

            <div class="relative w-full max-w-[600px] h-[300px] md:h-[450px] flex justify-center items-center my-4">
                <img loading="eager" :src="berryCan"
                    class="absolute left-[5%] md:left-[10%] w-[160px] md:w-[240px] -rotate-12 blur-[1px] opacity-70 transition-all duration-700 hover:-translate-x-5 drop-shadow-[0_20px_50px_rgba(155,77,150,0.3)] z-10" />
                
                <img loading="eager" :src="limeCan"
                    class="absolute right-[5%] md:right-[10%] w-[160px] md:w-[240px] rotate-12 blur-[1px] opacity-70 transition-all duration-700 hover:translate-x-5 drop-shadow-[0_20px_50px_rgba(0,255,162,0.3)] z-10" />
                
                <img loading="eager" :src="orangeCan"
                    class="relative w-[200px] md:w-[320px] z-20 animate-float drop-shadow-[0_30px_60px_rgba(255,107,53,0.5)]" />
            </div>

            <h2 class="text-4xl md:text-6xl font-black mb-8 uppercase italic tracking-tighter text-white">
                IGNITE YOUR <span class="text-spark-green">INNER FIRE</span>
            </h2>

            <button @click="scrollToFlavors"
                class="px-10 py-4 bg-white text-black font-black rounded-full hover:bg-spark-green transition-all hover:scale-105 cursor-pointer z-40">
                EXPLORE FLAVORS
            </button>
        </div>

        <div class="absolute bottom-8 left-1/2 -translate-x-1/2 opacity-30 flex flex-col items-center">
            <div class="w-[1px] h-12 bg-white animate-bounce"></div>
        </div>
    </section>
</template>