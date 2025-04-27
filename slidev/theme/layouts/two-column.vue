<script setup>
import { computed } from 'vue'
import Layouttextbox from "../components/citation.vue"
import SlideNumber from "../components/SlideNumber.vue"

const props = defineProps({
  titleText: { type: String, default: 'Default Title' },
  leftHeading: { type: String, default: '' },
  rightHeading: { type: String, default: '' },
  leftImage: { type: String, default: '' },
  rightImage: { type: String, default: '' },
  headerHeight: { type: [String, Number], default: 7.5 },
  headingRowHeight: { type: [String, Number], default: 7.5 },
  mainHeight: { type: [String, Number], default: 55 },
  textboxHeight: { type: [String, Number], default: 15 },
  spacerHeight: { type: [String, Number], default: 10 },
  reference: { type: String, default: '' },
})

// Compute dynamic grid layout
const gridTemplateRows = computed(() => {
  const header = props.headerHeight
  const hasSubheadings = props.leftHeading.trim() !== '' || props.rightHeading.trim() !== ''
  const headingRow = hasSubheadings ? props.headingRowHeight : 0
  const main = props.mainHeight + (hasSubheadings ? 0 : props.headingRowHeight)
  const textbox = props.textboxHeight
  const spacer = props.spacerHeight

  return `${header}% ${headingRow}% ${main}% ${textbox}% ${spacer}%`
})

// Two column layout in heading and main
const twoColumnGrid = computed(() => `repeat(2, minmax(0, 1fr))`)
</script>

<template>
  <div class="slidev-layout custom-layout" :style="{ gridTemplateRows }">
    
    <!-- Title -->
    <div class="flex flex-col justify-center gap-2">
      <h1 class="text-5xl font-bold text-[#24527a] leading-tight m-0 text-left">{{ titleText }}</h1>
    </div>

    <!-- Heading Row -->
    <div class="main-grid" :style="{ gridTemplateColumns: twoColumnGrid }">
      <!-- Left Subheading -->
      <div class="flex flex-col justify-center items-center">
        <h2 v-if="leftHeading" class="text-2xl font-semibold text-[#2B90B6] leading-snug m-0 text-center">
          {{ leftHeading }}
        </h2>
      </div>

      <!-- Right Subheading -->
      <div class="flex flex-col justify-center items-center">
        <h2 v-if="rightHeading" class="text-2xl font-semibold text-[#2B90B6] leading-snug m-0 text-center">
          {{ rightHeading }}
        </h2>
      </div>
    </div>

    <!-- Main Images or Slots -->
    <div class="main-grid" :style="{ gridTemplateColumns: twoColumnGrid }">
      <!-- Left Content -->
      <div class="flex flex-col justify-start items-center p-2 gap-2">
        <div v-if="leftImage" class="w-full flex justify-center">
          <img :src="leftImage" class="max-w-full max-h-64 object-contain rounded-2xl" />
        </div>
        <slot name="left" />
      </div>

      <!-- Right Content -->
      <div class="flex flex-col justify-start items-center p-2 gap-2">
        <div v-if="rightImage" class="w-full flex justify-center">
          <img :src="rightImage" class="max-w-full max-h-64 object-contain rounded-2xl" />
        </div>
        <slot name="right" />
      </div>
    </div>

    <!-- Text Underneath -->
    <div class="text-left text-base leading-tight">
      <slot name="text" />
    </div>

    <!-- Footer / Spacer -->
    <div class="flex items-center justify-center w-full">
      <Layouttextbox :reference="reference" />
    </div>

  </div>

  <SlideNumber />
</template>

<style lang="postcss">
:global(.slidev-layout) {
  @apply border-0 p-0 m-0 shadow-none !important;
}

.slidev-layout.custom-layout {
  @apply h-full w-full grid px-10 py-6 gap-4;
  background-image: url("../assets/full-branding.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}

/* Main two-column grid for headings and main */
.main-grid {
  display: grid;
  width: 100%;
  height: 100%;
  gap: 1rem;
}
</style>
