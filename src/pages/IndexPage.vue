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
        label="ชื่อ-สกุล *"
        hint="ชื่อและนามสกุล"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'กรุณาพิมพ์ชื่อ']"
      />
      <q-input
        filled
        type="number"
        v-model="age"
        label="อายุ *"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'กรุณาใส่อายุ',
          val => val > 0 && val < 100 || 'กรุณาใส่อายุจริง'
        ]"
      />
      <q-toggle v-model="accept" label="ยอมรับ" />
      <div>
        <q-btn label="ยอมรับ" type="submit" color="primary"/>
        <q-btn label="ยกเลิก" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
    </q-form>
  </div>
</template>

<script>
import { useQuasar } from 'quasar'
import { ref } from 'vue'

export default {
  setup () {
    const $q = useQuasar()
    const name = ref(null)
    const age = ref(null)
    const accept = ref(false)
    return {
      name,
      age,
      accept,
      onSubmit () {
        if (accept.value !== true) {
          $q.notify({
            color: 'red-5',
            textColor: 'white',
            icon: 'warning',
            message: 'คุณจำเป็นต้องยอมรับ'
          })
        }
        else {
          $q.notify({
            color: 'green-4',
            textColor: 'white',
            icon: 'cloud_done',
            message: 'ข้อมูลได้รับการยืนยัน'
          })
        }
      },
      onReset () {
        name.value = null
        age.value = null
        accept.value = false
      }
    }
  }
}
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
