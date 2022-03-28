<template>
    <div>
        <template v-for="(sale, index) of sales">
        <v-subheader
           :key="sale.id"
          v-text="sale.type"
        ></v-subheader>

        <v-divider
           :key="index"
        ></v-divider>

        <v-list-item
         :key="sale.weight"
        >
          <v-list-item-avatar>
            <v-img :src="require('@/static/' + sale.type + '_img.jpg')"></v-img>
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-title v-html="'Тип: ' + sale.type"></v-list-item-title>
            <v-list-item-subtitle v-html="'Город отправки: ' + sale.departure_city"></v-list-item-subtitle>
            <v-list-item-subtitle v-html="'Адрес отправки: ' + sale.departure_address"></v-list-item-subtitle>
            <v-list-item-subtitle v-html="'Город назначения: ' + sale.destination_city"></v-list-item-subtitle>
            <v-list-item-subtitle v-html="'Адрес назначения: ' + sale.destination_address"></v-list-item-subtitle>
            <v-list-item-subtitle v-html="'Вес товара: ' + sale.weight"></v-list-item-subtitle>
            <v-list-item-subtitle v-html="'Объём товара: ' + sale.volume"></v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </template>
    </div>
</template>

<script>
export default {
    props: ['sales'],
    name: 'Order'
}
</script>