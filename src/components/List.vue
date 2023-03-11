<!-- This example requires Tailwind CSS v2.0+ -->
<template>
  <div class="text-center">
      <h1 class="text-xl my-8">Simpson Quotes</h1>
      <!-- <SortButton direction="up" text="Sort ascending" />
      <SortButton direction="down" text="Sort descending" /> -->
      <section>
        <div class="row">
          <!-- Use semantic markup: article, figure-->
          <article
          v-for="quote in localQuotes"
          :key="quote"
          class="bg-gradient-to-br from-gray-200 rounded-lg shadow w-64"
        >
            <figure class="flex-1 flex flex-col p-8">
              <img 
              :src="quote.image"
              :alt="`image of ${quote.character}`"
              class="w-32 h-32 flex-shrink-0 mx-auto rounded-full shadow-xl bg-white"
              >
              <figcaption class="mt-6 text-gray-900 text-xs">
                  <q>{{ quote.quote }}</q>
                  <footer>—{{ quote.character }}</footer>
              </figcaption>
            </figure>
        </article>
        </div>
      </section>
  </div>
</template>

<script>
import SortButton from './SortButton.vue';
// fetch from https://thesimpsonsquoteapi.glitch.me/quotes
import data from '../data.json'
export default {
  name: 'Simpsons',
  components: { SortButton },
  setup() {
    return {
      localQuotes: data
    };
  },
};
</script>
