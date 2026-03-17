<!-- components/Navigation.vue -->
<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const activeSection = ref('hero')
const isScrolled = ref(false)

const scrollToSection = (sectionId) => {
    const element = document.getElementById(sectionId)
    if (element) {
        element.scrollIntoView({ behavior: 'smooth', block: 'start' })
    }
}

const handleScroll = () => {
    isScrolled.value = window.scrollY > 50

    const sections = ['hero', 'flavor', 'features', 'contact']
    let current = 'hero'
    const offset = window.scrollY + 120

    for (const section of sections) {
        const el = document.getElementById(section)
        if (!el) continue
        if (el.offsetTop <= offset) {
            current = section
        }
    }

    activeSection.value = current
}

onMounted(() => {
    window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
    window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
    <nav class="navigation" :class="{ 'scrolled': isScrolled }">
        <div class="nav-container">
            <div class="logo" @click="scrollToSection('hero')">
                ⚡ SPARK
            </div>

            <div class="nav-links">
                <button @click="scrollToSection('flavor')" :class="{ active: activeSection === 'flavor' }">
                    Flavor
                </button>
                <button @click="scrollToSection('features')" :class="{ active: activeSection === 'features' }">
                    Features
                </button>
                <button @click="scrollToSection('contact')" :class="{ active: activeSection === 'contact' }">
                    Contact
                </button>
            </div>

            <button class="nav-cta">
                Shop Now
            </button>
        </div>
    </nav>
</template>

<style scoped>
.navigation {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    z-index: 100;
    padding: 20px 40px;
    transition: all 0.3s;
}

.navigation.scrolled {
    background: rgba(0, 0, 0, 0.8);
    backdrop-filter: blur(20px);
    padding: 15px 40px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.nav-container {
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.logo {
    font-size: 24px;
    font-weight: 800;
    color: #00ffa2;
    cursor: pointer;
    transition: transform 0.3s;
}

.logo:hover {
    transform: scale(1.05);
}

.nav-links {
    display: flex;
    gap: 40px;
}

.nav-links button {
    background: none;
    border: none;
    color: white;
    font-size: 16px;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.3s;
    position: relative;
    padding: 5px 0;
}

.nav-links button::after {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    width: 0;
    height: 2px;
    background: #00ffa2;
    transition: width 0.3s;
}

.nav-links button:hover::after,
.nav-links button.active::after {
    width: 100%;
}

.nav-links button.active {
    color: #00ffa2;
}

.nav-cta {
    padding: 10px 24px;
    background: linear-gradient(135deg, #ff6b35, #f7931e);
    border: none;
    border-radius: 30px;
    color: white;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s;
}

.nav-cta:hover {
    transform: translateY(-2px);
    box-shadow: 0 10px 20px rgba(255, 107, 53, 0.3);
}

@media (max-width: 768px) {
    .navigation {
        padding: 15px 20px;
    }

    .nav-links {
        gap: 20px;
    }

    .nav-cta {
        display: none;
    }

    .logo {
        font-size: 20px;
    }
}
</style>