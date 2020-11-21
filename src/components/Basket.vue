<template>
  <v-container>
    <h2 class="display-2 mb-4">Basket</h2>

    <v-list two-line>
      <template v-for="(product, index) in products">
        <v-list-item :key="product.product_id" avatar>
          <v-list-item-avatar>
            <img :src="product.src">
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-title v-html="product.title"></v-list-item-title>
            <v-list-item-subtitle v-html="product.description"></v-list-item-subtitle>
          </v-list-item-content>

          <v-list-item>
            {{product.price}}
          </v-list-item>

          <v-list-item-action>
            <!-- <v-text-field label="Quantity" reverse :value="product.qty"></v-text-field> -->
          </v-list-item-action>

          <v-list-item>
            {{product.price * product.qty}}
          </v-list-item>

          <v-list-item-action>
            <v-btn icon ripple @click="deleteItem">
              <v-icon color="red lighten-1">delete</v-icon>
            </v-btn>
          </v-list-item-action>
        </v-list-item>

        <v-divider v-if="index + 1 < products.length" :key="index"></v-divider>
      </template>
    </v-list>

    <v-container>
      <v-btn color="success" larger style="float: right;" @click="goToPayment">Go to payment</v-btn>
    </v-container>
  </v-container>
</template>

<script>
  export default {
    data: () => ({
      
    }),
    computed: {
      products() {
        return this.$route.query
      }
    },
    methods: {
      deleteItem() {
        this.$router.push({
          name: "Home"
        })
      },
      goToPayment() {
        this.$router.push({
          name: "Home"
        })
      }
    }
  }
</script>

<style scoped>

</style>
