<template>
    <button class="btn">-{{ text }}-</button>
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
    }
  }
}
</script>
