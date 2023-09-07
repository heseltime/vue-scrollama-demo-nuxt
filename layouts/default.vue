<template>
  <div class="bg-gray-500 text-gray-100 text-center pt-12 pb-2 px-2">
    <h3 class="text-4xl uppercase mb-4 font-mono">"PostCity Theme"</h3>
    <h4 class="text-md"> A fork/template/mock up for scrollytelling with Scrollama. </h4>

    <div class="max-w-3xl w-full mx-auto px-8 pt-32">
    <div class="pb-64 text-center">
      <NuxtLink v-for="page in pages" :key="page" :to="page" class="underline mx-4">
        <span class="main-link" v-if="page == '/'">Composite Page</span>
        <span class="secondary-link" v-else>+ {{ page }}</span>
      </NuxtLink>

      <h4 class="text-md"> Scrollytelling elements as well as pages can be added in, the Offset bar ist just demonstrating the scrollytelling mechanism for now. </h4>
    </div>
    <Nuxt />

    <div
      class="fixed left-0 w-full h-0 border-t-2 border-dashed border-black"
      :style="{ top: triggerTop + 'px' }"
    >
      <p>Offset: {{ offset }}</p>
    </div>
  </div>
</div>

  
</template>

<script>
export default {
  data () {
    return {
      pages: ['/', 'Basic', 'Progress', 'StickyGraphic1', 'StickyGraphic2'],
      triggerTop: 0,
      offset: 0.6
    }
  },
  mounted () {
    window.addEventListener('resize', this.handleResize)
    this.handleResize()
  },
  methods: {
    handleResize () {
      this.triggerTop = this.offset * window.innerHeight
    }
  }
}
</script>

<style scoped>
.main-link {
  font-size: 2em;
}

.secondary-link {
  color: #bbb;
  text-decoration: none;
}
</style>