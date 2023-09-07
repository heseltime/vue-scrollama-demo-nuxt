<template>
  <div>

    <div> 

      <div class="banner">
        <h2>POSTCITY BANNER HERE</h2>
      </div>

       <div class="intro">
        <h3>INTRO HERE</h3>
      </div>

      <h3>Dramatic/Scrollytelling Intro Part: IDSA x Ars Electronica Introduce ...</h3>

      <div
        class="graphic sticky top-0 bg-gray-300 border border-black mt-20 flex items-center justify-center text-8xl"
      >
        {{ activeStepIdSticky }}
      </div>

      <Scrollama
        :offset="0.6"
        class="relative"
        @step-enter="stepEnterHandlerSticky"
      >
        <div
          v-for="step in stepsSticky"
          :key="step.id"
          :data-step-id="step.id"
          class="step my-64 h-48 w-48 mx-auto bg-yellow-300 border border-black flex justify-center items-center"
          @step-enter="stepEnterHandlerSticky"
        >
          Intro Step {{ step.id }}
        </div>
      </Scrollama>

    </div>

    <h3>Mutlidisciplinarity Part</h3>

    <div class="flex"> 

      <div
        class="graphic flex-1 sticky top-0 bg-gray-300 border border-black mt-20 flex items-center justify-center text-8xl"
      >
        {{ activeStepIdSticky2 }}
      </div>
      <Scrollama
        :offset="0.6"
        class="flex-1"
        @step-enter="stepEnterHandlerSticky2"
      >
        <div
          v-for="step in stepsSticky2"
          :key="step.id"
          :data-step-id="step.id"
          class="my-64 h-48 w-48 mx-auto bg-yellow-300 border border-black flex justify-center items-center"
          @step-enter="stepEnterHandlerSticky2"
        >
          Discipline {{ step.id }}
        </div>
      </Scrollama>
    </div>

    <Scrollama
        :offset="0.6"
        @step-enter="stepEnterHandler"
        @step-exit="stepExitHandler"
      >
        <div
          v-for="step in steps"
          :key="step.id"
          :data-step-id="step.id"
          class="my-64 h-48 border border-black flex justify-center items-center"
          :class="{ 'bg-yellow-300': activeStepId === step.id }"
        >
          Topic Group {{ step.id }}
        </div>
    </Scrollama>

    <div class="summary">
      <h3>SUMMARY HERE</h3>
    </div>

  </div>
</template>

<script>
export default {
  data () {
    return {
      steps: [{ id: '1' }, { id: '2' }, { id: '3' }, { id: '4' }, { id: '5' }, { id: '6' }],
      stepsSticky: [{ id: 'A' }, { id: 'B' }, { id: 'C' }, { id: 'D' }],
      stepsSticky2: [{ id: 'I' }, { id: 'II' }, { id: 'III' }, { id: 'IV' }],
      activeStepId: null,
      activeStepIdSticky: 'A',
      activeStepIdSticky2: 'I'
    }
  },
  methods: {
    stepEnterHandler ({ element, direction, index }) {
      console.log('step-enter', { element, direction, index })
      this.activeStepId = element.dataset.stepId
    },
    stepEnterHandlerSticky ({ element, direction, index }) {
      console.log('step-enter', { element, direction, index })
      this.activeStepIdSticky = element.dataset.stepId
    },
    stepEnterHandlerSticky2 ({ element, direction, index }) {
      console.log('step-enter', { element, direction, index })
      this.activeStepIdSticky2 = element.dataset.stepId
    },
    stepExitHandler ({ element, direction, index }) {
      console.log('step-exit', { element, direction, index })
      this.activeStepId = null
    }
  }
}
</script>

<style scoped>
.graphic {
  height: 80vh;
}

.banner {
  margin-bottom: 100px;
}

.intro {
  margin-bottom: 100px;
}

.summary {
  margin-bottom: 100px;
}
</style>