# PrimeVue slider bounds reproduction

Minimal Vue 3 and Vite reproduction, using the same SFC structure as the [PrimeVue issue template](https://stackblitz.com/edit/primevue-4-vite-issue-template).

[Open in StackBlitz](https://stackblitz.com/github/Xapollon430/primevue-slider-bounds-repro)

Run `npm install` and `npm run dev`. Press and hold the slider thumb for two seconds. The maximum changes from 100 to 60. Release without moving. PrimeVue 4.5.5 emits `slideend.value = 85`, outside the new bounds.

The expected release value is 60. `Reset` restores the initial state.
