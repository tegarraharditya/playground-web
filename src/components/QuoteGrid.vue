<template>
  <div class="row">
    <app-quote v-for="(quote, index) in quotes" :color="quote.color"
               @click.native="deleteQuote(index)"><p name="quoteText">{{ quote.quote }}</p>
    </app-quote>
  </div>
</template>

<script>
import Quote from './Quote.vue';

export default {
  props: ['quotes'],
  components: {
    appQuote: Quote
  },
  methods: {
    deleteQuote(index) {
      this.$emit('quoteDeleted', index);
    }
  }
}
</script>

<style>

</style>