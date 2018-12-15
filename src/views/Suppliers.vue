<template>
    <div>
        <h1>Order</h1>
 <b-table striped hover :items="orders" :fields="fields" :per-page="pagesize" :current-page="pageindex"></b-table>
  <b-pagination size="lg" :total-rows="orders.length" v-model="pageindex" :per-page="pagesize">  </b-pagination>
    </div>
</template>
<script>
import axios from "axios";
export default {
  name: "order",
  components: {},
  data() {
    return {
      message: " Final Project ",
      orders: [],
      pagesize:10,
      pageindex:1,
      fields: [
        { key: "supplier_id", sortable: true },
        { key: "company_name", sortable: true },
        { key: "contact_name", sortable: true },
        { key: "contact_title", sortable: true },
        { key: "address", sortable: true },
        { key: "city", sortable: true },
        { key: "region", sortable: true },
        { key: "postal_code", sortable: true },
        { key: "country", sortable: true },
        { key: "phone", sortable: true },
        { key: "fax", sortable: true }
        
      ]
    };
  },
  mounted() {
    var instace = this;
    axios
      .get("https://frozen-river-13804.herokuapp.com/api/Suppliers/")
      .then(function(response) {
        console.log(response.data);
        instace.orders = response.data.data;
      });
  }
};
</script>