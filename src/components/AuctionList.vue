<template>
  <div>
    <v-tabs v-model="activeTab">
      <v-tab v-for="(auctionGroup, index) in groupedData" :key="index">
        {{ formatBoroughName(auctionGroup.global.borough) }}{{formatLocationOrder(auctionGroup.global.location_order)}}
        <br>
        {{ formatDateString(auctionGroup.global.auction_date) }}
      </v-tab>
    </v-tabs>

    <v-tabs-items v-model="activeTab">
      <v-tab-item v-for="(auctionGroup, index) in groupedData" :key="index">
        <!-- Your Table Here -->
      </v-tab-item>
    </v-tabs-items>
  </div>
</template>


<script>
export default {
  name: "AuctionList",
  components: { },
  data() {
    return {
      activeTab: 0,
      search: '',
      groupedData: [],
      columns: [
        { label: 'Lot Number', value: 'lot_number' },
        { label: 'Year', value: 'model_year' },
        { label: 'Make', value: 'make' },
        { label: 'Model', value: 'model' },
        { label: 'Series/Trim', value: 'series_trim' },
        { label: 'VIN', value: 'vin' },
        { label: 'Lienholder', value: 'lienholder_name' }
      ],
    };
  },
  async created() {
    const response = await fetch('http://127.0.0.1:5000/api/get_cars');
    const rawData = await response.json();

    this.groupedData = rawData.map((item) => {
      const records = item.records;
      const rowCount = records.lienholder_name.length;
      const recordsArray = Array.from({ length: rowCount }, (_, rowIndex) => {
        return {
          lot_number: records.lot_number[rowIndex],
          model_year: records.model_year[rowIndex],
          make: records.make[rowIndex],
          model: records.model[rowIndex],
          series_trim: records.series_trim[rowIndex],
          vin: records.vin[rowIndex],
          lienholder_name: records.lienholder_name[rowIndex]
        };
      });
      return {
        global: item.global,
        recordsArray: recordsArray,
      };
    });
  },
  methods: {
    formatDateString(dateString) {
      const date = new Date(Date.parse(dateString.replace(" 00:00:00 GMT", "")));
      return `${date.getMonth() + 1}/${date.getDate()}/${date.getFullYear()}`;
    },
    formatBoroughName(borough) {
      let formattedBorough = borough.charAt(0).toUpperCase() + borough.slice(1);
      if (formattedBorough === 'Statenisland') {
        return 'Staten Island';
      }
      return formattedBorough;
    },
    formatLocationOrder(order) {
      if (order !== "1") {
        return " - " + order;
      } else {
        return "";
      }
    }
  }
}
</script>

<style scoped>
.table-container {
  overflow-x: auto;
  max-width: 100%;
}
</style>
