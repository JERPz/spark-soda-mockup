<!-- components/LoadingScreen.vue -->
<script setup>
import { ref, onMounted } from 'vue'

const loading = ref(true)
const progress = ref(0)

onMounted(() => {
    const interval = setInterval(() => {
        if (progress.value < 100) {
            progress.value += 10
        } else {
            clearInterval(interval)
            setTimeout(() => {
                loading.value = false
            }, 500)
        }
    }, 100)
})
</script>

<template>
    <Transition name="fade">
        <div v-if="loading" class="loading-screen">
            <div class="loading-content">
                <div class="spark-logo">⚡</div>
                <h1>SPARK SODA</h1>
                <div class="progress-bar">
                    <div class="progress-fill" :style="{ width: progress + '%' }"></div>
                </div>
            </div>
        </div>
    </Transition>
</template>

<style scoped>
.loading-screen {
    position: fixed;
    inset: 0;
    background: black;
    z-index: 1000;
    display: flex;
    align-items: center;
    justify-content: center;
}

.loading-content {
    text-align: center;
}

.spark-logo {
    font-size: 80px;
    animation: pulse 1.5s ease-in-out infinite;
    margin-bottom: 20px;
}

h1 {
    font-size: 36px;
    font-weight: 800;
    margin-bottom: 40px;
    background: linear-gradient(135deg, #ff6b35, #00ffa2);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
}

.progress-bar {
    width: 300px;
    height: 4px;
    background: rgba(255, 255, 255, 0.1);
    border-radius: 4px;
    overflow: hidden;
}

.progress-fill {
    height: 100%;
    background: linear-gradient(90deg, #ff6b35, #00ffa2);
    transition: width 0.3s ease;
    border-radius: 4px;
}

@keyframes pulse {

    0%,
    100% {
        transform: scale(1);
        opacity: 1;
    }

    50% {
        transform: scale(1.2);
        opacity: 0.7;
    }
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.5s;
}

.fade-enter-from,
.fade-leave-to {
    opacity: 0;
}
</style>
