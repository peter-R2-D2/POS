<template>
  <v-container 
    class="pa-6" 
    style="background-color: #0f1115;
    min-height: 100vh;"
  >
    <!-- Filas de paneles vacíos -->
    <v-row dense>
      <v-col
        cols="12" sm="6" md="3"
        v-for="n in 4" :key="'card-top-' + n"
      >
        <v-card 
          elevation="2"
          rounded="lg"
          class="pa-4"
          color="#1b1e24"
          height="120"
        />
      </v-col>
    </v-row>

    <v-row class="mt-6" dense>
      <v-col cols="12" md="8">
        <v-card
          elevation="2"
          rounded="lg"
          class="pa-4"
          color="#1b1e24"
          height="250"
        />
      </v-col>

      <v-col cols="12" md="4">
        <v-card
          elevation="2"
          rounded="lg"
          class="pa-4"
          color="#1b1e24"
          height="250"
        />
      </v-col>
    </v-row>
  </v-container>
</template>
