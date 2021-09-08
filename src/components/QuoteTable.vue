<template>
  <div>
    <div class="row" style="padding-left: 10px; padding-right: 10px">
      <button id="buttonShowTable" type="button" class="btn btn-primary" @mouseover="isTableShow = true">Hover to Show
        Table
      </button>
      <button id="buttonHideTable" type="button" class="btn btn-info" @mouseover="isTableShow = false">Hover to Hide
        Table
      </button>
      <button id="buttonShowAfterTen" type="button" class="btn btn-warning" @click="showAfterTenSec">Click to show table
        after 10 seconds
      </button>
    </div>
    <br>
    <div class="row" style="padding-left: 10px; padding-right: 10px">
      <table id="tableQuote" class="table table-bordered" v-if="isTableShow">
        <thead>
        <tr>
          <th>Quotes</th>
          <th>Color</th>
        </tr>
        </thead>
        <tbody>
        <tr name="tableRow" v-for="(quote, index) in quotes">
          <td name="tableColumnQuote">{{ quote.quote }}</td>
          <td name="tableColumnColor">{{ quote.color }}</td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>

export default {
  props: ['quotes'],
  data: function () {
    return {
      isTableShow: false
    }
  },
  methods: {
    showAfterTenSec() {
      setTimeout(() => this.isTableShow = true, 10000);
    }
  }
}
</script>

<style>

</style>