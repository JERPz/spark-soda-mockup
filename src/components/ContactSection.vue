<template>
    <section class="contact">
        <div class="container">
            <h2>Ready to Feel the Spark?</h2>
            <p class="subtitle">Join thousands of satisfied customers who have discovered their new favorite drink.</p>

            <div class="cta-section">
                <button class="cta-primary">
                    Shop Now - $2.99/can
                </button>
                <button class="cta-secondary">
                    Find Stores Near You
                </button>
            </div>

            <div class="contact-info">
                <div class="info-item">
                    <div class="icon">📧</div>
                    <div class="content">
                        <h4>Email Us</h4>
                        <p>hello@sparksoda.com</p>
                    </div>
                </div>

                <div class="info-item">
                    <div class="icon">📱</div>
                    <div class="content">
                        <h4>Follow Us</h4>
                        <p>@sparksoda</p>
                    </div>
                </div>

                <div class="info-item">
                    <div class="icon">🏆</div>
                    <div class="content">
                        <h4>Awards</h4>
                        <p>Best Energy Drink 2024</p>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
</script>

<style scoped>
.contact {
    padding: 120px 0;
    background: linear-gradient(135deg, #ff6b35 0%, #f7931e 50%, #00ffa2 100%);
    color: white;
    position: relative;
}

.contact::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(circle at 30% 70%, rgba(255, 255, 255, 0.1) 0%, transparent 50%),
        radial-gradient(circle at 70% 30%, rgba(0, 0, 0, 0.1) 0%, transparent 50%);
}

.container {
    max-width: 1000px;
    margin: 0 auto;
    padding: 0 20px;
    text-align: center;
    position: relative;
    z-index: 1;
}

h2 {
    font-size: 48px;
    font-weight: 800;
    margin-bottom: 16px;
}

.subtitle {
    font-size: 20px;
    opacity: 0.9;
    margin-bottom: 60px;
    max-width: 600px;
    margin-left: auto;
    margin-right: auto;
}

.cta-section {
    display: flex;
    gap: 24px;
    justify-content: center;
    margin-bottom: 80px;
    flex-wrap: wrap;
}

.cta-primary {
    padding: 18px 40px;
    background: rgba(255, 255, 255, 0.15);
    backdrop-filter: blur(20px);
    border: 1px solid rgba(255, 255, 255, 0.2);
    border-radius: 50px;
    color: white;
    font-weight: 700;
    font-size: 18px;
    transition: all 0.3s ease;
    cursor: pointer;
}

.cta-primary:hover {
    background: rgba(255, 255, 255, 0.25);
    transform: translateY(-2px);
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
}

.cta-secondary {
    padding: 18px 40px;
    background: transparent;
    border: 2px solid rgba(255, 255, 255, 0.3);
    border-radius: 50px;
    color: white;
    font-weight: 700;
    font-size: 18px;
    transition: all 0.3s ease;
    cursor: pointer;
}

.cta-secondary:hover {
    background: rgba(255, 255, 255, 0.1);
    border-color: rgba(255, 255, 255, 0.5);
    transform: translateY(-2px);
}

.contact-info {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 40px;
}

.info-item {
    display: flex;
    align-items: center;
    gap: 20px;
    padding: 30px;
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(20px);
    border-radius: 20px;
    border: 1px solid rgba(255, 255, 255, 0.2);
    transition: all 0.3s ease;
}

.info-item:hover {
    transform: translateY(-5px);
    background: rgba(255, 255, 255, 0.15);
}

.icon {
    font-size: 32px;
}

.content {
    text-align: left;
}

.content h4 {
    font-size: 18px;
    font-weight: 700;
    margin-bottom: 4px;
}

.content p {
    opacity: 0.9;
    font-size: 16px;
}

@media (max-width: 768px) {
    .contact {
        padding: 80px 0;
    }

    h2 {
        font-size: 36px;
    }

    .cta-section {
        flex-direction: column;
        align-items: center;
    }

    .cta-primary,
    .cta-secondary {
        width: 100%;
        max-width: 300px;
    }

    .contact-info {
        grid-template-columns: 1fr;
        gap: 20px;
    }

    .info-item {
        padding: 20px;
    }
}
</style>