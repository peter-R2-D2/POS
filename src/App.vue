<template>
  <v-app>
    <v-layout>
      <v-app-bar
        v-if="$vuetify.display.mobile"
        color="secodary"
      >
        <v-toolbar-title>Nombre del negocio</v-toolbar-title>
        <v-app-bar-nav-icon
          variant="text"
          @click.stop="drawer = !drawer"
        />
      </v-app-bar>
      <v-navigation-drawer
        v-model="drawer"
        :location="$vuetify.display.mobile ? 'start' : undefined"
        :class="{
          'position-relative': !$vuetify.display.mobile,
          'position-absolute': $vuetify.display.mobile
        }"
      >
        <v-list
          :lines="false"
          nav
        >
          <v-list-item
            v-for="(item, i) in items"
            :key="i"
            :value="item"
            color="primary"
            :to="item.value"
          >
            <template #prepend>
              <v-icon :icon="item.icon" />
            </template>

            <!-- eslint-disable -->
            <v-list-item-title v-text="item.title" />
            <!-- eslint-enable -->
          </v-list-item>
        </v-list>
      </v-navigation-drawer>

      <v-container>
        <router-view />
      </v-container>
    </v-layout>


    <AppFooter />
  </v-app>
</template>

<script setup>
  import AppFooter from '@/components/AppFooter.vue'
  import { useDisplay } from 'vuetify'
  import { ref, watch } from 'vue'


  const { mobile } = useDisplay()

  const items = [
    {
      title: 'Inicio',
      value: '/',
      icon: 'mdi-home', 
    },
    {
      title: 'Ventas',
      value: '/ventas',
      icon: 'mdi-cart',
    },
    {
      title: 'Inventario',
      value: '/inventario',
      icon: 'mdi-archive',
    },
    {
      title: 'Egresos',
      value: '/egresos',
      icon: 'mdi-cash-minus',
    },
  ]

  const drawer = ref(mobile.value ? false : true)
  const group = ref(null)

  watch(group, () => {
    drawer.value = false
  })
</script>
