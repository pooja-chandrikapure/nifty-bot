<template>
    <div class="min-h-screen bg-black relative overflow-hidden flex items-center justify-center">
        <!-- Background Pattern -->
        <div class="absolute inset-0 opacity-10">
            <div class="grid grid-cols-12 gap-4 transform rotate-12 scale-150">
                <div v-for="i in 144" :key="i"
                    class="w-8 h-8 border border-green-500 rounded flex items-center justify-center text-green-500 text-xs">
                    {{ patternIcons[(i - 1) % 10] }}
                </div>
            </div>
        </div>

        <!-- Main Card -->
        <div
            class="relative z-10 bg-gray-900 rounded-2xl py-8 px-4 w-full max-w-md mx-4 shadow-2xl border border-gray-800">
            <!-- Profile Circle -->
            <div class="flex justify-center mb-4">
                <div @click="redirectToTg"
                    class="cursor-pointer w-20 h-20 bg-black rounded-full border-2 border-white flex items-center justify-center">
                    <img src="/icon2.jpeg" class="rounded-full" alt="">
                </div>
            </div>

            <!-- Title -->
            <h1 class="text-white text-2xl font-bold text-center mb-0 ">
                NIFTY BOT
            </h1>

            <!-- Subtitle -->
            <h2 class="text-gray-400 text-[14px] font-bold text-center mb-3 ">
                (Index Trading Automation)
            </h2>
            <h2 class="text-white text-[14px] font-semibold text-center mb-2 leading-tight">
                ⚡ High-Speed Entry/Exit Bot
            </h2>

            <!-- Key Features Header -->
            <div class="text-white text-sm mb-3 text-center">
                <p class="mt-3 text-md font-medium flex items-center justify-center gap-2">
                    🤖 INDEX ALGO – 100% Automated Trading System
                </p>
                <p class="mt-3 text-md font-medium flex items-center justify-center gap-2">
                    🔑 Learn how traders use technology for smarter decisions
                </p>
                <p class="text-gray-400 mt-2 text-md font-medium flex items-center justify-center gap-2">
                    (100% Educational | No financial advice)
                </p>
            </div>
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
              <p class="text-white text-center my-6 font-medium">
                    👇🏻 Click on the below link to join the community 👇🏻
              </p>
              <!-- <p class="text-white text-center my-6 font-medium">
                  🚀Join our FREE Channel to see the Magic unfold! 🚀
                </p> -->
                
                <!-- Join Button with Shine Effect -->
                <div class="flex justify-center">
                    <button @click="redirectToTg"
                    class="join-button bg-blue-600 hover:bg-blue-700 text-white font-semibold py-3 px-8 rounded-full transition-all duration-300 overflow-hidden transform hover:scale-105">
                    <span class="relative z-10">Join Now</span>
                    <!-- Shine Effect -->
                    <div
                    class="shine-overlay absolute inset-0 bg-gradient-to-r from-transparent via-white/30 to-transparent transform -translate-x-full skew-x-12">
                </div>
            </button>
        </div>
        <!-- <p class="text-center my-6 font-medium text-red-400 text-2xl">
              Invitation closes in {{ countdown }}s
        </p> -->

            <!-- Updated Content -->
            <div class="text-[12px] text-white/40 leading-tight mt-4 text-center">
               Disclaimer: This community and the content shared inside are strictly for educational purposes. 
               We do not provide financial, investment, or trading advice.
                Index trading involves risk, and past results do not guarantee future outcomes. 
                Always consult your financial advisor and follow proper risk management before trading.
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";


const START_TIME = 10; // seconds
const countdown = ref(START_TIME);
let timer = null;

onMounted(() => {
  timer = setInterval(() => {
    if (countdown.value > 0) {
      countdown.value--;
    } else {
      countdown.value = START_TIME; // 🔁 reset (loop)
    }
  }, 1000);
});
onUnmounted(() => {
    clearInterval(timer);
});
// const redirectToTg = () => {
//     window.open('https://telegram.me/+6OF3nvW5gdVkY2I1', '_blank')
// }
const redirectToTg = () => {
    const params = new URLSearchParams(window.location.search)
    const campaign = params.get('utm_campaign')

    let telegramLink = "https://t.me/+v0csWHba34lhMjY1"  // default (original link)

    if (campaign === "camp1") {
        telegramLink = "https://t.me/+v0csWHba34lhMjY1"
    } else if (campaign === "camp2") {
        telegramLink = "https://t.me/+ByqRz_MgVJs4NmZl"
    } else if (campaign === "camp3") {
        telegramLink = "https://t.me/+Ey1TxP6PQ6w5YWY1"
    } else if (campaign === "camp4") {
        telegramLink = "https://t.me/+WYfZXeGRrY85ZjRl"
    }

    if (window.fbq) {
        window.fbq('track', 'Subscribe', {
            campaign: campaign || "default"
        })
    }

    window.open(telegramLink, '_blank')
}
const patternIcons = ['📊', '💰', '📈', '🎯', '⚡', '💹', '📋', '⏰', '🔔', '💎']
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

/* Background animation */
.bg-black {
    background: radial-gradient(ellipse at center, #1a1a2e 0%, #000000 70%);
}
</style>
