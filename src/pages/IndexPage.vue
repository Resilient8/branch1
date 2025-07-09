<template>
  <div class="q-pa-md" style="max-width: 400px">
    <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="q-gutter-md"
    >
      <q-input
        filled
        v-model="name"
        label="Your name *"
        hint="Name and surname"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Please type something']"
      />
      <q-input
        filled
        type="number"
        v-model="age"
        label="Your age *"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'Please type your age',
          val => val > 0 && val < 100 || 'Please type a real age'
        ]"
      />
      <q-toggle v-model="accept" label="I accept the license and terms" />
      <div>
        <q-btn label="Submit" type="submit" color="primary"/>
        <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
    </q-form>
  </div>
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
