<template>
  <div>
    <v-row class="text-center">
      <v-col cols="12" class="">
        <v-data-table
          :headers="columnas"
          :items="info.data"
          class="elevation-5 rounded-0"
          :items-per-page="20"
          :search="search"
          :custom-filter="filterOnlyCapsText"
          dark
        >
          <template v-slot:top>
            <v-text-field
              v-model="search"
              label="Search Coins"
              class="mx-4 mt-0"
            ></v-text-field>
          </template>
          <!-- headers :: columnas -->
          <template v-slot:item.image="{ item }">
            <div class="p-2">
              <ul>
                <li>
                  <v-img
                    :src="item.image"
                    :alt="item.name"
                    height="42px"
                    width="42px"
                  ></v-img>
                </li>
                <li>
                  <v-chip
                    color="cyan"
                    dark
                    small
                    class="ml-4"
                    style="color: black"
                  >
                    {{ item.symbol }}
                  </v-chip>
                </li>
              </ul>
            </div>
          </template>

          <template v-slot:item.current_price="{ item }">
               <span color="green" class="text-green ">  {{ formatPrice(item.current_price)}} <strong class="text-white "> USD </strong> </span>
          </template>

           


          <template v-slot:item.last_updated="{ item }">
               <span color="green" class="text-green ">  {{ formatDate(item.last_updated) }} </span>
          </template>
        </v-data-table>

        
      </v-col>
    </v-row>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "HelloWorld",
  data: () => ({
    info: [],
    search: "",

    columnas: [
      {
        text: "ID",
        align: "left",
        sortable: false,
        value: "market_cap_rank",
      },
      { text: "Logo", align: "left", value: "image", sortable: false },
      { text: "Nombre", align: "left", value: "name", sortable: false },
      { text: "Precio", align: "left", value: "current_price" },
      { text: "MAXPrecio", align: "left", value: "market_cap" },
      { text: "Precio Cambiado 24h", align: "left", value: "price_change_24h" },
      { text: "Ultima Actualizacion", align: "left", value: "last_updated" },
    ],
    desserts: [
      {
        name: "Frozen Yogurt",
        image:
          "https://assets.coingecko.com/coins/images/1/large/bitcoin.png?1547033579",
        calories: 159,
        fat: 6.0,
        carbs: 24,
        protein: 4.0,
        iron: "1%",
      },
      {
        name: "Frozen Yogurt",
        image:
          "https://assets.coingecko.com/coins/images/1/large/bitcoin.png?1547033579",
        calories: 159,
        fat: 6.0,
        carbs: 24,
        protein: 4.0,
        iron: "1%",
      },
    ],
  }),
  mounted() {
    axios
      .get("https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd")
      .then((response) => (this.info = response));
  },
  methods:
   {
   formatPrice(value) {
        let val = (value/1).toFixed(2).replace('.', ',')
        return val.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".")
    },
      formatDate(date) {
    return new Intl.DateTimeFormat('es-US', { dateStyle: 'long' }).format(new Date(date))
  },
  
    GetDatosCoins() {},
  }
};
</script>
<style lang="scss" scoped>
ul {
  display: flex;
  justify-content: left;
  align-items: center;
  padding: 3px;
}
ul > li {
  display: inline-block;
  /* You can also add some margins here to make it look prettier */
}

.text-green{
  color:cyan;
}
</style>
