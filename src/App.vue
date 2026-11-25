<script setup>
import { ref } from 'vue';
import Slider from 'primevue/slider';
const value = ref(85);
const max = ref(100);
const committed = ref(null);
function start() {
    committed.value = null;
    setTimeout(() => { max.value = 60; }, 1200);
}
function reset() { max.value = 100; value.value = 85; committed.value = null; }
</script>
<template>
  <main>
    <h1>Slider drag-end bounds reproduction</h1>
    <p>Press and hold the thumb for two seconds. The maximum drops from 100 to 60. Release without moving.</p>
    <div @mousedown.capture="start" @touchstart.capture="start" @click.capture.stop>
      <Slider v-model="value" :max="max" @slideend="committed = $event.value" />
    </div>
    <p>Maximum: {{ max }} | Model: {{ value }} | Slide end: {{ committed ?? 'not released' }}</p>
    <p>Expected: slide end and model are at most 60. Actual: slide end is 85.</p>
    <button @click="reset">Reset</button>
  </main>
</template>
<style>body{font:18px system-ui;margin:4rem auto;max-width:48rem;padding:2rem} .p-slider{margin:3rem 0}</style>
