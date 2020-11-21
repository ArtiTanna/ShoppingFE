<template>
  <v-container>
    <SearchFront @search="search" @clearSearch="clearSearch"/>
    <h2 class="display-2 mb-4">Products</h2>

    <v-layout row wrap>
      <template v-for="(product, index) in products">
        <v-flex xs2 pa-1 :key="index">
          <v-hover>
            <v-card slot-scope="{hover}" class="mx-auto" color="gray lighten-4" max-width="600" height="350">
              <v-img :src="product.src" :aspect-ratio="16/9">
                <v-expand-transition>
                  <div v-if="hover" class="d-flex transition-fast-in-fast-out orange draken-2 display-3 v-card--reveal display3 black--text" style="height: 100%;">
                    {{product.price}}
                  </div>
                </v-expand-transition>
              </v-img>

              <v-card-text class="pt-4" style="position: relative;">
                <v-btn absolute color="orange" class="white--text" fab medium right top @click="addToBasket(product)">
                  <v-icon>shopping_cart</v-icon>
                </v-btn>

                <div class="font-weight-light grey--text title mb-2">{{product.category}}</div>
                <h3 class="display-1 font-weight-light orange--text mb-2">{{product.title}}</h3>

                <div class="font-weight-light mb-2">{{product.description}}</div>
              </v-card-text>

              <v-btn icon ripple @click="deleteItem(product)">
                <v-icon color="red lighten-1">delete</v-icon>
              </v-btn>

              
            </v-card>
          </v-hover>
        </v-flex>
      </template>
    </v-layout>
    <v-btn color="primary" v-if="products.length === 0" @click="addItem()">
      Add Products
    </v-btn>
  </v-container>
</template>

<script>
import SearchFront from '@/components/shared/search-front'
  export default {
    data: () => ({
      products: [{
        price: 14000,
        src: 'https://cdn.vuetifyjs.com/images/cards/kitchen.png',
        category: 'Mobile',
        title: 'MI Note 4',
        description: 'Test Description',
        product_id: 1
      },{
        price: 150000,
        src: 'https://cdn.vuetifyjs.com/images/cards/kitchen.png',
        category: 'Mobile',
        title: 'MI Note 7',
        description: 'Test Description',
        product_id: 2
      },{
        price: 12000,
        src: 'https://cdn.vuetifyjs.com/images/cards/kitchen.png',
        category: 'Electronics',
        title: 'MI TV',
        description: 'Test Description',
        product_id: 3
      },{
        price: 12000,
        src: 'https://cdn.vuetifyjs.com/images/cards/kitchen.png',
        category: 'Electronics',
        title: 'HP Laptop',
        description: 'Test Description',
        product_id: 4
      },{
        price: 12000,
        src: 'https://cdn.vuetifyjs.com/images/cards/kitchen.png',
        category: 'Electronics',
        title: 'Dell Laptop',
        description: 'Test Description',
        product_id: 5
      },{
        price: 12000,
        src: 'https://cdn.vuetifyjs.com/images/cards/kitchen.png',
        category: 'Electronics',
        title: 'LG',
        description: 'Test Description',
        product_id: 6
      }]
    }),
    methods: {
      search(param) {
         /* eslint-disable */
        console.log('search ', param)
        console.log('products', this.products)
        if(param !== '') {
          this.products = this.products.filter(product=>product.title === param)
        }
       
        console.log('products', this.products)
      },
      clearSearch() {
        this.products = [{
        price: 14000,
        src: 'https://cdn.vuetifyjs.com/images/cards/kitchen.png',
        category: 'Mobile',
        title: 'MI Note 4',
        description: 'Test Description',
        product_id: 1
      },{
        price: 150000,
        src: 'https://cdn.vuetifyjs.com/images/cards/kitchen.png',
        category: 'Mobile',
        title: 'MI Note 7',
        description: 'Test Description',
        product_id: 2
      },{
        price: 12000,
        src: 'https://cdn.vuetifyjs.com/images/cards/kitchen.png',
        category: 'Electronics',
        title: 'MI TV',
        description: 'Test Description',
        product_id: 3
      },{
        price: 12000,
        src: 'https://cdn.vuetifyjs.com/images/cards/kitchen.png',
        category: 'Electronics',
        title: 'HP Laptop',
        description: 'Test Description',
        product_id: 4
      },{
        price: 12000,
        src: 'https://cdn.vuetifyjs.com/images/cards/kitchen.png',
        category: 'Electronics',
        title: 'Dell Laptop',
        description: 'Test Description',
        product_id: 5
      },{
        price: 12000,
        src: 'https://cdn.vuetifyjs.com/images/cards/kitchen.png',
        category: 'Electronics',
        title: 'LG Washingmachine',
        description: 'Test Description',
        product_id: 6
      }]
      },
      addToBasket(product) {
        /* eslint-disable */
        console.log('product ', product)
        let products = [];
        products.push(product);
        console.log('product ', products)
        this.$router.push({
          name:'Basket',
          query: products
        })
      },
      deleteItem(param) {
        /* eslint-disable */
        console.log('product ', param)
        console.log('product 1 ', this.products)
        console.log('param.product_id-----', param.product_id)
        this.products = this.products.filter(product=>product.product_id !== param.product_id)
        console.log('product 2', this.products)
      }
    },
    components: {
      SearchFront,
    }
  }
</script>

<style scoped>
.v-card--reveal {
  align-items: center;
  bottom: 0;
  justify-content: center;
  opacity: 0.5;
  position: absolute;
  width: 100%; 
}

.v-card h3.display-1 {
  font-size: 24px !important;
}
</style>
