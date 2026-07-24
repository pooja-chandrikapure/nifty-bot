<template>
    <div class="min-h-screen bg-hero relative overflow-hidden flex items-center justify-center py-10">
        <!-- Background Pattern -->
        <div class="absolute inset-0 opacity-[0.06]">
            <div class="grid grid-cols-12 gap-4 transform rotate-12 scale-150">
                <div v-for="i in 144" :key="i"
                    class="w-8 h-8 border border-blue-400 rounded flex items-center justify-center text-blue-400 text-xs">
                    {{ patternIcons[(i - 1) % 10] }}
                </div>
            </div>
        </div>

        <!-- Ambient glow accents -->
        <div class="glow-top"></div>
        <div class="glow-bottom"></div>

        <!-- Main Card -->
        <div
            class="relative z-10 bg-gray-900/90 backdrop-blur-sm rounded-2xl py-8 px-4 w-full max-w-md mx-4 shadow-2xl border border-white/10">

            <!-- Profile Circle -->
            <div class="flex justify-center mb-4">
                <div @click="redirectToTg"
                    class="cursor-pointer w-20 h-20 bg-black rounded-full border-2 border-white flex items-center justify-center ring-4 ring-blue-500/20">
                    <img src="/icon3.jpeg" class="rounded-full" alt="">
                </div>
            </div>

            <!-- Title -->
            <h1 class="text-center mb-1 text-3xl font-extrabold tracking-tight">
                <span class="text-white">NIFTY </span>
                <span class="bg-gradient-to-r from-blue-400 to-purple-500 bg-clip-text text-transparent">BOT</span>
            </h1>

            <!-- Subtitle -->
            <h2 class="text-blue-300/80 text-[14px] font-medium text-center mb-3">
                ( Index Trading Automation )
            </h2>

            <div class="flex items-center justify-center gap-2 mb-1">
                <div class="w-16 h-px bg-gradient-to-r from-transparent via-blue-500/50 to-transparent"></div>
            </div>

            <!-- <h2 class="text-white text-[15px] font-semibold text-center mb-4 flex items-center justify-center gap-2">
                <span>⚡</span> High-Speed Entry/Exit Bot
            </h2> -->
            <div class="flex justify-center mb-4">
                <div class=" text-white border border-purple-400/40 rounded-full px-4 py-2 flex items-center gap-2 text-sm">
                    <span>⚡</span> High-Speed Entry/Exit Bot
                </div>
            </div>
            <!-- Key Features Header -->
            <div class="text-white text-sm mb-3 text-center">
                <p class="mt-3 text-md font-medium flex items-center justify-center gap-2">
                    🤖 INDEX ALGO – 100% Automated Trading System
                </p>
                <!-- <p class="mt-3 text-md font-medium flex items-center justify-center gap-2">
                    🔑 Learn how traders use technology for smarter decisions
                </p> -->
                <p class="text-gray-400 mt-2 text-md font-medium flex items-center justify-center gap-2">
                    (100% Educational | No financial advice)
                </p>
            </div>

            <!-- Index Algo Pill -->
            <!-- <div class="flex justify-center mb-4">
                <div class="border border-purple-400/40 rounded-full px-4 py-2 flex items-center gap-2 text-sm">
                    <span>🤖</span>
                    <span class="text-white font-medium">INDEX ALGO –</span>
                    <span class="text-emerald-400 font-semibold">100% Automated</span>
                    <span class="text-white font-medium">Trading System</span>
                </div>
            </div> -->

            <!-- Educational note -->
            <!-- <div class="text-white text-sm mb-5 text-center px-2">
                <p class="font-medium flex items-center justify-center gap-2 leading-snug">
                    <span>🎓</span>
                    <span>Learn how traders use technology for smarter decisions</span>
                </p>
                <p class="text-gray-400 mt-2 text-xs">
                    ( 100% Educational | No financial advice )
                </p>
            </div> -->


            <!-- Important Warning -->
                <div class="bg-red-500/10 border border-red-500/30 rounded-lg p-3 mt-5 text-sm text-white text-center">
                    ⚠️ <span class="font-semibold">IMPORTANT:</span> Don’t Miss This Step  
                    <br /><br />
                    Most users click the button but forget to tap <b>"JOIN"</b> inside Telegram  
                    <br /><br />
                    ❌ If you don’t tap JOIN, access will not be available  
                    <br /><br />
                    👉 Smart traders complete the final step and get instant access
                </div>

            <!-- Join Channel Text -->
            <p class="text-white text-center mt-4 mb-4 font-medium text-sm">
                👇 Click on the below link to join the community 👇
            </p>

            <!-- Join Button with Shine Effect -->
            <div class="flex justify-center">
                <button @click="redirectToTg"
                    class="join-button text-white font-semibold py-3 px-10 rounded-full transition-all duration-300 overflow-hidden transform hover:scale-105 flex items-center gap-2">
                    <svg viewBox="0 0 24 24" class="w-5 h-5 relative z-10" fill="currentColor">
                        <path d="M21.5 2.5L2.5 10l6 2.5m13-10L15 20l-6.5-7.5m13-10L8.5 12.5" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                    </svg>
                    <span class="relative z-10">Open Telegram & Join Now</span>
                    <div
                        class="shine-overlay absolute inset-0 bg-gradient-to-r from-transparent via-white/30 to-transparent transform -translate-x-full skew-x-12">
                    </div>
                </button>
            </div>

            <!-- Countdown Timer -->
            <div class="flex justify-center mt-4">
                <div class="bg-white/5 border border-white/10 rounded-full px-4 py-1.5 flex items-center gap-2">
                    <span class="text-gray-300 text-xs font-semibold tracking-wide">ENDS IN:</span>
                    <span class="text-red-500 text-xs font-bold tabular-nums">{{ formattedCountdown }}</span>
                </div>
            </div>

            <!-- Disclaimer -->
            <div class="flex items-start gap-2 mt-6 bg-white/[0.02] border border-white/10 rounded-xl p-3">
                <span class="text-blue-400 flex-shrink-0 mt-0.5">🛡️</span>
                <p class="text-[11px] text-white/40 leading-tight">
                    Disclaimer: This community and the content shared inside are strictly for educational purposes.
                    We do not provide financial, investment, or trading advice. Index trading involves risk, and
                    past results do not guarantee future outcomes. Always consult your financial advisor and follow
                    proper risk management before trading.
                </p>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from "vue";

const START_TIME = 120; // 2 minutes, in seconds
const countdown = ref(START_TIME);
let timer = null;

const formattedCountdown = computed(() => {
    const minutes = Math.floor(countdown.value / 60);
    const seconds = countdown.value % 60;
    return `${String(minutes).padStart(2, '0')}:${String(seconds).padStart(2, '0')}`;
});

onMounted(() => {
    timer = setInterval(() => {
        if (countdown.value > 0) {
            countdown.value--;
        } else {
            countdown.value = START_TIME; // loop restart
        }
    }, 1000);
});
onUnmounted(() => {
    clearInterval(timer);
});

const redirectToTg = () => {
    const params = new URLSearchParams(window.location.search);
    const campaign = params.get('utm_campaign');

    let telegramLink = "https://t.me/+v0csWHba34lhMjY1"; // default (original link)

    if (campaign === "camp1") {
        telegramLink = "https://t.me/+v0csWHba34lhMjY1";
    // } else if (campaign === "camp2") {
    //     telegramLink = "https://t.me/+GR9e4wp_zfwwYmY1"
    // } else if (campaign === "camp3") {
    //     telegramLink = "https://t.me/+2qT3h40yT9FiM2I1"
    // } else if (campaign === "camp4") {
    //     telegramLink = "https://t.me/+SjXso73_SZtlNjc9"
    }

    if (window.fbq) {
        window.fbq('track', 'Subscribe', {
            campaign: campaign || "default"
        });
    }

    window.open(telegramLink, '_blank');
};

const patternIcons = ['📊', '💰', '📈', '🎯', '⚡', '💹', '📋', '⏰', '🔔', '💎'];

// Feature grid data — icons are simple stroke paths (clock, rocket, shield-check, bar-chart)
const features = [
    {
        title: 'AUTOMATED',
        subtitle: '100% Automated Trading System',
        color: '#a78bfa',
        icon: '<circle cx="12" cy="12" r="9"/><path d="M12 7v5l3 3"/>'
    },
    {
        title: 'HIGH SPEED',
        subtitle: 'Lightning-fast Entry & Exit',
        color: '#818cf8',
        icon: '<path d="M14.5 2c-2 3-2 6-1 8-3 1-6 4-8 9 5-2 8-1 9-1 2-3 2-7 1-9 1-3 1-5-1-7Z"/><circle cx="9" cy="15" r="1.2" fill="currentColor" stroke="none"/>'
    },
    {
        title: 'RELIABLE',
        subtitle: 'Built for Accuracy & Consistency',
        color: '#34d399',
        icon: '<path d="M12 3l7 3v6c0 4.5-3 8-7 9-4-1-7-4.5-7-9V6l7-3Z"/><path d="M9 12l2 2 4-4"/>'
    },
    {
        title: 'SMART DECISIONS',
        subtitle: 'Technology-driven Trading Edge',
        color: '#f472b6',
        icon: '<path d="M4 19h16"/><path d="M7 19v-5"/><path d="M12 19v-9"/><path d="M17 19v-6"/><path d="M14 5l6 1-1 6"/><path d="M20 6l-6 6-3-3-5 5"/>'
    }
];
</script>

<style scoped>
@keyframes shine {
    0% {
        transform: translateX(-100%) skewX(-15deg);
    }

    100% {
        transform: translateX(200%) skewX(-15deg);
    }
}

.join-button:hover .shine-overlay {
    animation: shine 0.8s ease-in-out;
}

.join-button {
    position: relative;
    background: linear-gradient(45deg, #0f46bd, #286ddd);
    box-shadow: 0 4px 15px rgba(37, 99, 235, 0.3);
}

.join-button:hover {
    box-shadow: 0 6px 20px rgba(37, 99, 235, 0.4);
    transform: scale(1.05) translateY(-1px);
}

.join-button::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
    animation: shine-continuous 3s infinite;
    z-index: 1;
}

@keyframes shine-continuous {
    0% {
        left: -100%;
    }

    50% {
        left: 100%;
    }

    100% {
        left: 100%;
    }
}

/* Background: deep navy radial gradient */
.bg-hero {
    background:
        radial-gradient(circle at 50% 0%, rgba(37, 99, 235, 0.25) 0%, transparent 45%),
        radial-gradient(ellipse at center, #10152b 0%, #05070f 70%);
}

.glow-top {
    position: absolute;
    top: -120px;
    left: 50%;
    transform: translateX(-50%);
    width: 600px;
    height: 400px;
    background: radial-gradient(circle, rgba(59, 130, 246, 0.35) 0%, transparent 70%);
    filter: blur(60px);
    pointer-events: none;
}

.glow-bottom {
    position: absolute;
    bottom: -150px;
    right: -100px;
    width: 500px;
    height: 400px;
    background: radial-gradient(circle, rgba(99, 102, 241, 0.2) 0%, transparent 70%);
    filter: blur(80px);
    pointer-events: none;
}

/* Phone illustration in the warning card */
.phone-mockup {
    position: relative;
    width: 64px;
    padding: 10px 6px;
    border-radius: 16px;
    border: 2px solid;
    border-image: linear-gradient(160deg, #3b82f6, #ec4899) 1;
    background: rgba(255, 255, 255, 0.02);
}

.phone-glow {
    position: absolute;
    inset: -10px;
    background: radial-gradient(circle, rgba(59, 130, 246, 0.25) 0%, transparent 70%);
    filter: blur(10px);
    pointer-events: none;
    z-index: -1;
}
</style>
