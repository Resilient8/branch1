<template>
  <q-page class="flex flex-center q-pa-md bg-dark text-white">
    <div class="column items-center q-gutter-y-lg q-py-xl">
      <img
        alt="Quasar logo"
        src="~assets/quasar-logo-vertical.svg"
        style="width: 250px; height: 250px;"
        class="animated-logo q-mb-md"
      >
      <img
        alt="Quasar logo"
        src="~assets/quasar-logo-vertical.svg"
        style="width: 250px; height: 250px;"
        class="animated-logo q-mb-md"
      >
       <img
        alt="Quasar logo"
        src="~assets/quasar-logo-vertical.svg"
        style="width: 250px; height: 250px;"
        class="animated-logo q-mb-md"
      >

      <div class="text-h3 text-weight-bold text-center q-mt-lg">
        Welcome to Quasar!
      </div>
      <div class="text-h6 text-center text-grey-4 q-mb-lg" style="max-width: 600px;">
        Crafting amazing apps with elegant and powerful solutions.
      </div>

      <q-btn
        label="EXPLORE MORE"
        color="primary"
        icon="arrow_forward"
        size="lg"
        class="q-mt-md"
        to="/about"
        glossy
        outline
      />
    </div>

    <div class="background-pulse-enhanced"></div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'IndexPage'
})
</script>

<style lang="scss">
// SASS Variables for easier theme management
$primary-color: #2196F3; // Quasar's default primary blue

// CSS สำหรับแอนิเมชันโลโก้
.animated-logo {
  animation: float 4s ease-in-out infinite; // Slower animation
  transform-origin: center;
  filter: drop-shadow(0 0 10px rgba($primary-color, 0.6)); // Add a subtle glow
}

@keyframes float {
  0% { transform: translateY(0px); }
  50% { transform: translateY(-20px); } // Increased float distance
  100% { transform: translateY(0px); }
}

// CSS สำหรับพื้นหลังเท่ๆ ที่มองเห็นชัดเจนขึ้น
.background-pulse-enhanced {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 700px; // Larger size
  height: 700px; // Larger size
  background: radial-gradient(circle at center, rgba($primary-color, 0.15) 0%, rgba($primary-color, 0) 70%); // More subtle gradient
  border-radius: 50%;
  transform: translate(-50%, -50%);
  animation: pulse-enhanced 12s ease-in-out infinite; // Slower pulse
  z-index: -1; // Make sure it's behind content
  opacity: 0.8; // Make it a bit more visible
}

@keyframes pulse-enhanced {
  0% { transform: translate(-50%, -50%) scale(0.9); opacity: 0.6; }
  50% { transform: translate(-50%, -50%) scale(1.1); opacity: 0.4; }
  100% { transform: translate(-50%, -50%) scale(0.9); opacity: 0.6; }
}

// Adjustments for dark background
.bg-dark {
  background-color: #121212 !important; // A true dark background
}
.text-grey-4 {
  color: #bdbdbd !important; // Lighter grey for better contrast
}
</style>
