<script setup>
defineProps({
  title: {
    type: String,
    default: 'test of what is would like to be a very long title',
  },
})
</script>

<template>
  <div class="slidev-layout mainer">
    <div
      style="position: absolute; z-index: 100; left: 2.5%; top: 2.5%; width: 95%; height: 10%; transform-origin: left left; transform: rotate(0deg); border: 1px solid black;"
    >
      <h1 style="text-align: left;">{{ title }}</h1>
    </div>
    <div class="main-body" style="position: absolute; top: 15%; left: 2.5%; width: 95%; height: 73%; border: 1px solid black;">
      <slot />
    </div>
  </div>
</template>

<style lang="postcss">
.slidev-layout.mainer {
  background-image: url("../assets/full-branding.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;

  @apply text-center py-15 h-full grid;

  h1 {
    @apply text-6xl leading-15;
  }
}
</style>
