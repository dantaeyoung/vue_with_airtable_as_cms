<template>
  <div id="app">
    <AirtableDisplayExample :records="records" />
  </div>
</template>

<script>
import AirtableDisplayExample from "./components/AirtableDisplayExample.vue";

const process_api_key = process.env.VUE_APP_AIRTABLE_API_KEY;
const airtable_table = process.env.VUE_APP_AIRTABLE_TABLE;
const airtable_base = process.env.VUE_APP_AIRTABLE_BASE;
const airtable_view = process.env.VUE_APP_AIRTABLE_VIEW ;

export default {
  name: "App",
  components: {
    AirtableDisplayExample
  },
  data: function() {
    return {
      records: []
    };
  },
  created() {
    this.loadAirtableData();
  },
  methods: {
    loadAirtableData() {
      var Airtable = require("airtable");
      var base = new Airtable({ apiKey: process_api_key }).base(airtable_base);
      let records = [];
      var self = this;

      base(airtable_table)
        .select({
          view: airtable_view,
        })
        .eachPage(
          function page(partialRecords, fetchNextPage) {
            records = [...records, ...partialRecords]
            fetchNextPage();
          },
          function done(err) {
            console.log("done", records);
            self.records = records;
            if (err) {
              console.error(err);
              return;
            }
          }
        );
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
