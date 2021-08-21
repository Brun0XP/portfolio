<template>
  <div class="relative flex items-top justify-center sm:items-center sm:pt-0">
    <div class="max-w-4xl mx-auto sm:px-6 lg:px-8">
      <div class="mt-12 md:mt-52 grid grid-cols-1 md:grid-cols-12">
        <div class="mx-8 md:mx-0 overflow-hidden p-6 col-span-7">
          <h2 class="text-3xl leading-7 text-gray-50 font-semibold">
            Hi There!
            <span class="wave">👋🏻</span>
          </h2>
          <p class="text-4xl mt-6 text-gray-50">
            I'M <span class="text-purple-500 font-bold">BRUNO RODRIGUES</span>
          </p>
          <Typewriter :type-array="messages" />
        </div>
        <img
          src="@/assets/images/home-main.svg"
          class="flex justify-center pt-8 sm:pt-0 col-span-5"
        />
      </div>

      <div class="mb-12 mt-52 mx-6 grid grid-cols-1 md:grid-cols-12">
        <div class="col-span-8 text-gray-50">
          <h2 class="pb-8 text-4xl text-center">
            LET ME <span class="text-purple-500">INTRODUCE</span> MYSELF
          </h2>

          <p class="text-xl pb-4">
            I fell in love with programming and I have at least learnt
            something, I think… 🤷‍♂️
          </p>

          <p class="text-xl pb-4">
            I am fluent in classics like
            <span class="text-purple-500">Java, Javascript and C#.</span>
          </p>

          <p class="text-xl pb-4">
            My field of Interest's are building new
            <span class="text-purple-500">Web Technologies and Products</span>
            and also
            <span class="text-purple-500"
              >creating practical solutions for companies and people..</span
            >
          </p>

          <p class="text-xl">
            Whenever possible, I also apply my passion for developing products
            with <span class="text-purple-500">Node.js</span> and
            <span class="text-purple-500"
              >Modern Javascript Library and Frameworks like Vue.js and
              Nuxt.js</span
            >
          </p>
        </div>
        <div class="mt-8 col-span-4 p-8">
          <img
            src="https://avatars.githubusercontent.com/u/36716331?v=4"
            alt=""
          />
        </div>
      </div>

      <h2 class="text-4xl leading-7 text-gray-50 font-semibold text-center">
        FIND ME ON
      </h2>
      <p class="text-gray-50 text-center mt-2">
        Feel free to <span class="text-purple-500">connect</span> with me
      </p>
      <div class="flex justify-center my-8 space-x-4 text-xl text-purple-500">
        <a
          v-for="(link, index) in links"
          :key="index"
          :href="link.url"
          target="_blank"
          class="
            bg-gray-50
            w-8
            h-8
            rounded-full
            flex
            items-center
            justify-center
          "
        >
          <i :class="link.icon" />
        </a>
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
    links: [
      {
        name: 'Linkedin',
        url: 'https://www.linkedin.com/in/bruno-r-611b45121/',
        icon: 'mdi mdi-linkedin',
      },
      {
        name: 'GitLab',
        url: 'https://gitlab.com/Brun0XP',
        icon: 'mdi mdi-gitlab',
      },
      {
        name: 'GitHub',
        url: 'https://github.com/Brun0XP',
        icon: 'mdi mdi-github',
      },
      {
        name: 'Instagram',
        url: 'https://instagram.com/bds.rodrigues',
        icon: 'mdi mdi-instagram',
      },
    ],
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

<style>
html {
  font-family: Nunito;
}

.wave {
  animation: wave-animation 2.1s infinite;
  transform-origin: 70% 70%; /* Pivot around the bottom-left palm */
  display: inline-block;
}

@keyframes wave-animation {
  0% {
    transform: rotate(0deg);
  }
  10% {
    transform: rotate(14deg);
  }
  20% {
    transform: rotate(-8deg);
  }
  30% {
    transform: rotate(14deg);
  }
  40% {
    transform: rotate(-4deg);
  }
  50% {
    transform: rotate(10deg);
  }
  60% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(0deg);
  }
}
</style>
