<template>
  <v-card
    class="mx-auto"
  >
    <v-card-text>
      <div class="text--primary">
        <div class="subtitle-1 font-weight-medium ">
          {{ title }}
        </div>
        <div class="display-1 font-weight-bold text-right">
          Rp. {{ data.total }}
        </div>
      </div>
    </v-card-text>
    <v-divider />
    <v-card-actions>
      <div class="caption">
        <v-icon color="grey lighten-1">
          mdi-calendar-clock
        </v-icon> Last 24 hours
      </div>
      <v-btn icon v-on="on">
        <v-icon color="grey lighten-1">
          mdi-dots-horizontal
        </v-icon>
      </v-btn>
    </v-card-actions>
  </v-card>
</template>
<script>
export default {
  props: {
    data: {
      type: Object,
      required: true
    },
    title: {
      type: String,
      required: true
    }
  }
}
</script>
