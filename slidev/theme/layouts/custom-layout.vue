<script setup>
import Layouttextbox from "../components/citation.vue";

const props = defineProps({
  titleText: {
    type: String,
    default: 'Default Title',
  },
  subtitleText: {
    type: String,
    default: 'Default Subtitle',
  },
  image: {
    type: String,
    required: false,
  },
  headerHeight: {
    type: [String, Number],
    default: 15,
  },
  mainHeight: {
    type: [String, Number],
    default: 55,
  },
  textboxHeight: {
    type: [String, Number],
    default: 15,
  },
  spacerHeight: {
    type: [String, Number],
    default: 10,
  },
  reference: {
    type: String,
    default: 'Default Reference',
  },
})
</script>

<template>
    <div class="slidev-layout custom-layout">
      <!-- Title and Subtitle Area -->
      <div class="header">
        <h1 class="title">{{ titleText }}</h1>
        <h2 class="subtitle">{{ subtitleText }}</h2>
      </div>
  
      <!-- Main Content Area -->
      <div class="main-body">
        <div class="w-full flex justify-center items-center p-8" style="height: 100%;">
          <div class="relative w-full h-full max-w-2xl max-h-96">
            <img v-if="image"
                 :src="image"
                 class="absolute inset-0 m-auto max-w-full max-h-full rounded-2xl object-contain" />
            <slot v-else />
          </div>
        </div>
      </div>
  
      <!-- Textbox Content Area -->
      <div class="textbox-content">
        <slot name="text" />
      </div>
  
      <!-- Spacer Area -->
      <div class="spacer">
        <Layouttextbox :reference="reference" />
      </div>
    </div>
</template>

<style lang="postcss">
.slidev-layout.custom-layout {
  @apply h-full w-full grid gap-4 px-10 py-6;
  background-image: url("../assets/full-branding.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  /* Create 4 rows: Header, Main, textbox, Spacer */
  grid-template-rows: v-bind('`${headerHeight}% ${mainHeight}% ${textboxHeight}% ${spacerHeight}%`');
}

.main-body {
    @apply flex justify-center items-center w-full h-full overflow-hidden;
    border: none;
  }

/* Header: Title + Subtitle */
.header {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  gap: 0.25rem;
}

/* Title */
.title {
  font-size: 2.8rem; /* relative size - safe */
  font-weight: bold;
  margin: 0;
  padding: 0;
  line-height: 1.1; /* tight line height */
  color: #24527a;
}

/* Subtitle */
.subtitle {
  font-size: 1.5rem;
  font-weight: 500;
  margin: 0;
  padding: 0;
  color: #2B90B6;
  line-height: 1.2;
}

/* Main Content */
.main-content {
  @apply flex justify-center items-center;
  overflow: hidden;
  border: none;
}

/* textbox Content */
.textbox-content {
  text-align: left;
  font-size: 1rem;
  line-height: 1.2;
  padding: 0;
  margin: 0;
  display: block;
}

.textbox-content p, .textbox-content li {
  margin: 0;
  padding: 0;
  line-height: 1.2;
}

/* Spacer */
.spacer {
  /* This section is a flexible spacer */
}

.main-content {
    @apply flex justify-center items-center;
    overflow: hidden;
    border: none;
  }

</style>
