<template>
    <button class="btn" @click="sort">-{{ text }}-</button>
</template>
<script>
// make the button work, so that it will sort according to the `direction` prop
export default {
  data() {
    return {
      sortedQuotes: null
    }
  },
  props: {
    text: {
      required: true,
      type: String
    },
    direction: {
      required: true,
      type: String
    },
    data: {
      required: true,
      type: Array
    }
  },
  methods: {
    sort() {
      console.log(this.data);
      this.direction === "up" ? this.sortAsc() : this.sortDesc();
      this.$emit("sorted", this.sortedQuotes);
    },
    sortAsc() {
      this.sortedQuotes = this.data.sort((a,b)=> a.character.localeCompare(b.character));
    },
    sortDesc() {
      this.sortedQuotes = this.data.sort((a,b)=> b.character.localeCompare(a.character));
    }

  }
}
</script>
