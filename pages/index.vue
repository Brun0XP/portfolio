<template>
  <div class="bg-gray-900">
    <vue-particles color="#B968C7" class="fixed w-full h-full" />
    <div
      class="
        relative
        flex
        items-top
        justify-center
        min-h-screen
        sm:items-center sm:pt-0
      "
    >
      <div class="max-w-4xl mx-auto sm:px-6 lg:px-8">
        <div class="mt-12 mx-8 overflow-hidden p-6">
          <h2 class="text-3xl leading-7 text-gray-50 font-semibold">
            Hi There!
          </h2>
          <p class="text-4xl mt-6 text-gray-50">
            I'M <span class="text-purple-500">BRUNO RODRIGUES</span>
          </p>
          <div class="text-xl mt-16 text-purple-500 relative">
            <transition name="fade">
              <p
                :key="messageIndex"
                class="absolute"
                v-text="messages[messageIndex]"
              />
            </transition>
          </div>
        </div>

        <img
          src="@/assets/images/home-main.svg"
          class="flex justify-center pt-8 sm:pt-0"
        />
        <div class="flex justify-center pt-4 space-x-4 text-xl text-gray-300">
          <a href="https://instagram.com/bds.rodrigues" target="_blank">
            <i class="mdi mdi-instagram" />
          </a>
          <a href="https://twitter.com/" target="_blank">
            <i class="mdi mdi-twitter" />
          </a>
          <a href="https://github.com/Brun0XP" target="_blank">
            <i class="mdi mdi-github" />
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    messages: [
      'Open Source Contributor',
      'Fast-learn developer',
      'Self-taught developer',
    ],
    messageIndex: 0,
  }),
  mounted() {
    setInterval(() => {
      this.messageIndex =
        this.messageIndex === this.messages.length - 1
          ? 0
          : this.messageIndex + 1
    }, 5000)
  },
}
</script>

<style scoped>
.fade-enter-active {
  animation: fade-in-out 1s;
}
.fade-leave-active {
  animation: fade-in-out 1s reverse;
}

@keyframes fade-in-out {
  0% {
    opacity: 0;
  }
  50% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
