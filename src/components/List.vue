<!-- This example requires Tailwind CSS v2.0+ -->
<template>
  <h1 class="text-xl mb-8">Simpson Quotes</h1>
  <!-- <SortButton direction="up" text="Sort ascending" />
  <SortButton direction="down" text="Sort descending" /> -->
  <div
    v-for="quote in simpsons"
    :key="quote"
    class="bg-gradient-to-br from-gray-200 rounded-lg shadow w-64"
  >
    <div class="flex-1 flex flex-col p-8">
      <img
        class="w-32 h-32 flex-shrink-0 mx-auto rounded-full shadow-xl bg-white"
        :src="quote.image"
        alt="image of quote.character"
      />
      <h3 class="mt-6 text-gray-900 text-xs">
        {{ quote.quote }}
      </h3>
    </div>
  </div>
</template>

<script>
import SortButton from './SortButton.vue';
// fetch from https://thesimpsonsquoteapi.glitch.me/quotes
const simpsons = [
  {
    quote:
      'By chilling my loins I increase the chances of impregnating my wife.',
    character: 'Apu Nahasapeemapetilon',
    image:
      'https://cdn.glitch.me/3c3ffadc-3406-4440-bb95-d40ec8fcde72/ApuNahasapeemapetilon.png',
    characterDirection: 'Left',
  },
  {
    quote:
      'By chilling my loins I increase the chances of impregnating my wife.',
    character: 'Apu Nahasapeemapetilon',
    image:
      'https://cdn.glitch.me/3c3ffadc-3406-4440-bb95-d40ec8fcde72/ApuNahasapeemapetilon.png',
    characterDirection: 'Left',
  },
];

export default {
  name: 'Simpsons',
  components: { SortButton },
  setup() {
    return {
      simpsons,
    };
  },
};
</script>
