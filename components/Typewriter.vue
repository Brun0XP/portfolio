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

<script lang="ts">
export default {
    setup() {
        const typeValue = ''
        const typeStatus = false
        const typingSpeed = 100
        const erasingSpeed = 50
        const newTextDelay = 2000
        const typeArrayIndex = 0
        const charIndex = 0
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
    }
}
</script>