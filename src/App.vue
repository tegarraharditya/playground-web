<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdded="newQuote"></app-new-quote>
    <ul class="nav nav-tabs">
      <li :class="isActive('Grid')"><a id="gridView" href="#" @click="switchTab('Grid')">Grid
        View</a></li>
      <li :class="isActive('Table')"><a id="tableView" href="#" @click="switchTab('Table')">Table
        View</a></li>
    </ul>
    <br>
    <div class="panel panel-default">
      <div class="panel-body">
        <app-quote-grid v-if="activeTab === 'Grid'" :quotes="quotes"
                        @quoteDeleted="deleteQuote"></app-quote-grid>
        <app-quote-table v-if="activeTab === 'Table'" :quotes="quotes"></app-quote-table>
        <div class="row">
          <div class="col-sm-12 text-center" v-if="activeTab === 'Grid'">
            <div class="alert alert-info">Info: Click on a Quote to delete it!</div>
          </div>
        </div>
      </div>
    </div>
    <div class="footer-copyright text-center py-3">Powered By
      <a id="poweredBy" href="https://www.atlasid.tech/" target="_blank"> Atlas ID</a>
    </div>
  </div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid.vue';
import QuoteTable from './components/QuoteTable.vue';
import NewQuote from './components/NewQuote.vue';
import Header from './components/Header.vue';

export default {
  data: function () {
    return {
      quotes: [
        {quote: 'You Can do it!!!', color: 'white'}
      ],
      activeTab: 'Grid',
      maxQuotes: 10
    }
  },
  methods: {
    isActive(data) {
      if (this.activeTab === data) {
        return 'active'
      }
      return ''
    },
    switchTab(data) {
      this.activeTab = data;
    },
    newQuote(quote) {
      if (this.quotes.length >= this.maxQuotes) {
        return alert('Please delete Quotes first!');
      }
      if (quote.quote.length !== 0) {
        this.quotes.push(quote);
      }
    },
    deleteQuote(index) {
      this.quotes.splice(index, 1);
    }
  },
  components: {
    appQuoteGrid: QuoteGrid,
    appQuoteTable: QuoteTable,
    appNewQuote: NewQuote,
    appHeader: Header
  }
}
</script>

<style>
</style>
