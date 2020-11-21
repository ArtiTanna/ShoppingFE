<template>
    <div>
        <v-navigation-drawer v-model="drawer" app temporary>
        <v-list>
            <v-list-item>
            <v-list-item-content>
                <v-list-item-title>
                Menu
                </v-list-item-title>
            </v-list-item-content>
            </v-list-item>
            <v-divider></v-divider>

            <template v-for="(item, index) in items">
            <v-list-item :key="index" :href="item.href">
                <v-list-item-action>
                <v-icon light v-html="item.icon"></v-icon>
                </v-list-item-action>
                <v-list-item-action>
                <v-list-item-title v-html="item.title"></v-list-item-title>
                </v-list-item-action>
            </v-list-item>
            </template>
        </v-list>
        </v-navigation-drawer>

        <v-toolbar dark>
            <v-toolbar-side-icon @click="drawer = !drawer"></v-toolbar-side-icon>
            <v-spacer></v-spacer>

            <v-toolbar-items>
                <v-btn text>
                Products
                </v-btn>
                <v-btn text :to="{name: 'Basket'}">
                    <v-icon>shopping_cart</v-icon> Basket
                </v-btn>
            </v-toolbar-items>
        </v-toolbar>
    </div>
</template>

<script>
export default {
    data: () => ({
        drawer: false,
        items: [{
            icon: 'perm_identity',
            href: '#',
            title: 'Account'
      }]
    })
}
</script>

<style>

</style>