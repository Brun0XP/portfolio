<template>
  <p class="text-xl md:text-3xl mt-16 text-purple-500">
    <span> {{ typeValue }}</span
    ><span
      class="cursor inline-block m-0.5 w-0.5 bg-purple-500"
      :class="{ typing: typeStatus }"
      >&nbsp;</span
    >
  </p>
</template>

<script>
export default {
  props: {
    typeArray: {
      type: Array,
      required: true,
    },
  },
  data: () => ({
    typeValue: '',
    typeStatus: false,
    typingSpeed: 100,
    erasingSpeed: 50,
    newTextDelay: 2000,
    typeArrayIndex: 0,
    charIndex: 0,
  }),
  created() {
    setTimeout(this.typeText, this.newTextDelay + 200)
  },
  methods: {
    typeText() {
      if (this.charIndex < this.typeArray[this.typeArrayIndex].length) {
        if (!this.typeStatus) this.typeStatus = true

        this.typeValue += this.typeArray[this.typeArrayIndex].charAt(
          this.charIndex
        )
        this.charIndex += 1

        setTimeout(this.typeText, this.typingSpeed)
      } else {
        this.typeStatus = false
        setTimeout(this.eraseText, this.newTextDelay)
      }
    },
    eraseText() {
      if (this.charIndex > 0) {
        if (!this.typeStatus) this.typeStatus = true

        this.typeValue = this.typeArray[this.typeArrayIndex].substring(
          0,
          this.charIndex - 1
        )
        this.charIndex -= 1
        setTimeout(this.eraseText, this.erasingSpeed)
      } else {
        this.typeStatus = false
        this.typeArrayIndex += 1
        if (this.typeArrayIndex >= this.typeArray.length)
          this.typeArrayIndex = 0
        setTimeout(this.typeText, this.typingSpeed + 1000)
      }
    },
  },
}
</script>

<style scoped>
p span.cursor {
  animation: cursorBlink 1s infinite;
}

p span.typing {
  animation: none;
}

@keyframes cursorBlink {
  49% {
    background-color: #8b5cf6;
  }
  50% {
    background-color: transparent;
  }
  99% {
    background-color: transparent;
  }
}
</style>
