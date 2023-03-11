<!-- This example requires Tailwind CSS v2.0+ -->
<template>
  <div>
    <div v-if="asyncState==='loaded'" class="text-center">
      <h1 class="text-xl my-8">Simpson Quotes</h1>

      <!-- the child components need the data to sort it, 
      so i passed it through props-->
      <section>
        <SortButton direction="up" text="Sort ascending" :data="APIQuotes" 
        @sorted="sort"
        :class="[direction === 'up' ? 'active': '']">
        </SortButton>

        <SortButton direction="down" text="Sort descending" :data="APIQuotes" 
        @sorted="sort" 
        :class="[direction === 'down' ? 'active': '']">
      </SortButton>
      </section>

      <section>
        <div class="row">
          <!-- Use semantic markup: article, figure-->
          <article
          v-for="quote in APIQuotes"
          :key="quote._id"
          class="bg-gradient-to-br from-gray-200 rounded-lg shadow w-64 flex items-center justify-center h-full"
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

        <!-- group buttons in a section's' footer
        buttons are used because js is needed here-->
        <footer class="mt-8">
          <button class="btn" @click.once="loadQuotesCount(5)">5 Quotes are good</button>
          <button class="btn" @click.once="loadQuotesCount(10)">10 Quotes are good</button>
          <button class="btn" @click.once="loadQuotesCount(15)">15 Quotes are good</button>
        </footer>
      </section>

    </div>

    <!-- Add loading while fetching data-->
    <div v-else class="flex justify-center items-center">
      <img src="../assets/spinner.svg" alt="spinner-img">
      <span>Please wait..</span>
    </div>
  </div>
</template>

<script>
import SortButton from './SortButton.vue';
// fetch from https://thesimpsonsquoteapi.glitch.me/quotes
import data from '../data.json'
export default {
  name: 'Simpsons',
  components: { SortButton },
  data() {
    return {
      localQuotes: data,
      apiUrl: `https://thesimpsonsquoteapi.glitch.me/quotes`,
      APIQuotes: null,
      count: 3,
      asyncState: null,
      direction: null
    };
  },
  methods: {
    async fetchData(api, count) {
      this.asyncState = 'panding';
      // axios would be easier, i used fetch because it is already integrated in vuejs
      const data = await fetch(`${api}?count=${count}`);
      const jsonData = await data.json();
      this.APIQuotes = jsonData;
      this.asyncState = 'loaded';
    },
    loadQuotesCount(num) {
      this.count = +num;
      this.fetchData(this.apiUrl, this.count);
    },
    sort(payload) {
      console.log(payload)
      this.APIQuotes= payload.sortedQuotes;
      this.direction = payload.direction;
    }
  },
  created() {
    // upon vue instance creation, fetch the data from API
    this.fetchData(this.apiUrl, this.count);
  }
};
</script>
<style>
.btn.active {
  background-color: darkblue;
}
</style>