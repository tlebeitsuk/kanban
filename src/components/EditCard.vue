<template>
  <transition appear name="fade-shrink-in">
    <div class="fixed inset-0 w-full h-screen flex items-center justify-center bg-semi">
      <div class="relative w-full max-w-2xl bg-white shadow-lg rounded-lg p-5">
        <h2 class="text-lg pb-1 text-gray-800">{{data.title}}</h2>
        <div class="flex items-center text-gray-600" v-if="data.duedate">
          <div class="w-4 h-4 mr-1 fill-current">
            <svg viewBox="0 0 20 20">
              <path
                d="M10.25,2.375c-4.212,0-7.625,3.413-7.625,7.625s3.413,7.625,7.625,7.625s7.625-3.413,7.625-7.625S14.462,2.375,10.25,2.375M10.651,16.811v-0.403c0-0.221-0.181-0.401-0.401-0.401s-0.401,0.181-0.401,0.401v0.403c-3.443-0.201-6.208-2.966-6.409-6.409h0.404c0.22,0,0.401-0.181,0.401-0.401S4.063,9.599,3.843,9.599H3.439C3.64,6.155,6.405,3.391,9.849,3.19v0.403c0,0.22,0.181,0.401,0.401,0.401s0.401-0.181,0.401-0.401V3.19c3.443,0.201,6.208,2.965,6.409,6.409h-0.404c-0.22,0-0.4,0.181-0.4,0.401s0.181,0.401,0.4,0.401h0.404C16.859,13.845,14.095,16.609,10.651,16.811 M12.662,12.412c-0.156,0.156-0.409,0.159-0.568,0l-2.127-2.129C9.986,10.302,9.849,10.192,9.849,10V5.184c0-0.221,0.181-0.401,0.401-0.401s0.401,0.181,0.401,0.401v4.651l2.011,2.008C12.818,12.001,12.818,12.256,12.662,12.412"
              />
            </svg>
          </div>
          <div class="text-xs">{{ data.duedate }}</div>
        </div>
        <div class="py-2">
          <span class="text-sm text-gray-700">{{ data.description }}</span>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'editCard',
  props: ['data']
}
</script>

<style scoped>
.bg-semi {
  background: rgba(0, 0, 0, 0.5);
}
.fade-shrink-in-enter-active,
.fade-shrink-in-leave-active {
  transition: all 0.3s ease;
}

.fade-shrink-in-enter,
.fade-shrink-in-leave-to {
  opacity: 0;
  transform: scale(1.1);
}
</style>
