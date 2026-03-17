<template>
    <section class="testimonials">
        <div class="container">
            <h2>What Our Sparkers Say</h2>
            <p class="subtitle">Real experiences from real people</p>

            <div class="testimonials-slider">
                <div class="testimonials-track">
                    <div class="testimonial-card">
                        <div class="stars">★★★★★</div>
                        <p class="quote">"Spark Soda changed my morning routine. The Orange Blast gives me the perfect
                            energy boost without the jitters!"</p>
                        <div class="author">
                            <div class="name">Sarah M.</div>
                            <div class="title">Fitness Enthusiast</div>
                        </div>
                    </div>

                    <div class="testimonial-card">
                        <div class="stars">★★★★★</div>
                        <p class="quote">"Finally, a soda that tastes amazing and doesn't make me feel guilty. Berry
                            Spark is my new obsession!"</p>
                        <div class="author">
                            <div class="name">Mike R.</div>
                            <div class="title">Software Developer</div>
                        </div>
                    </div>

                    <div class="testimonial-card">
                        <div class="stars">★★★★★</div>
                        <p class="quote">"The Lime Charge keeps me refreshed during long work sessions. Natural energy
                            that actually works!"</p>
                        <div class="author">
                            <div class="name">Emma L.</div>
                            <div class="title">Designer</div>
                        </div>
                    </div>

                    <!-- Duplicate for seamless loop -->
                    <div class="testimonial-card">
                        <div class="stars">★★★★★</div>
                        <p class="quote">"Spark Soda changed my morning routine. The Orange Blast gives me the perfect
                            energy boost without the jitters!"</p>
                        <div class="author">
                            <div class="name">Sarah M.</div>
                            <div class="title">Fitness Enthusiast</div>
                        </div>
                    </div>

                    <div class="testimonial-card">
                        <div class="stars">★★★★★</div>
                        <p class="quote">"Finally, a soda that tastes amazing and doesn't make me feel guilty. Berry
                            Spark is my new obsession!"</p>
                        <div class="author">
                            <div class="name">Mike R.</div>
                            <div class="title">Software Developer</div>
                        </div>
                    </div>

                    <div class="testimonial-card">
                        <div class="stars">★★★★★</div>
                        <p class="quote">"The Lime Charge keeps me refreshed during long work sessions. Natural energy
                            that actually works!"</p>
                        <div class="author">
                            <div class="name">Emma L.</div>
                            <div class="title">Designer</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
</script>

<style scoped>
.testimonials {
    padding: 120px 0;
    background: linear-gradient(135deg, #0f0f0f 0%, #1a1a1a 100%);
    color: white;
}

.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 20px;
    text-align: center;
}

h2 {
    font-size: 48px;
    font-weight: 800;
    margin-bottom: 16px;
    background: linear-gradient(135deg, #ff6b35, #00ffa2);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
}

.subtitle {
    font-size: 20px;
    opacity: 0.8;
    margin-bottom: 80px;
}

.testimonials-slider {
    overflow: hidden;
    width: 100%;
}

.testimonials-track {
    display: flex;
    gap: 40px;
    animation: slideLeft 30s linear infinite;
    width: calc(400px * 6);
    /* 6 cards total */
}

.testimonial-card {
    flex: 0 0 400px;
    background: rgba(255, 255, 255, 0.05);
    backdrop-filter: blur(20px);
    border: 1px solid rgba(255, 255, 255, 0.1);
    border-radius: 20px;
    padding: 40px;
    transition: all 0.3s ease;
    position: relative;
}

@keyframes slideLeft {
    0% {
        transform: translateX(0);
    }

    100% {
        transform: translateX(-50%);
    }
}

.testimonial-card::before {
    content: '"';
    position: absolute;
    top: 20px;
    left: 30px;
    font-size: 60px;
    color: rgba(255, 255, 255, 0.1);
    font-family: serif;
}

.stars {
    color: #ffd700;
    font-size: 20px;
    margin-bottom: 24px;
}

.quote {
    font-size: 18px;
    line-height: 1.6;
    margin-bottom: 32px;
    font-style: italic;
    opacity: 0.9;
}

.author {
    border-top: 1px solid rgba(255, 255, 255, 0.1);
    padding-top: 24px;
}

.name {
    font-weight: 700;
    font-size: 18px;
    margin-bottom: 4px;
}

.title {
    opacity: 0.7;
    font-size: 14px;
    text-transform: uppercase;
    letter-spacing: 1px;
}

@media (max-width: 768px) {
    .testimonials {
        padding: 80px 0;
    }

    h2 {
        font-size: 36px;
    }

    .testimonials-track {
        width: calc(300px * 6);
        gap: 20px;
    }

    .testimonial-card {
        flex: 0 0 300px;
        padding: 30px;
    }
}
</style>