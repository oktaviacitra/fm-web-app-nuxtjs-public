<template>
  <v-card>
    <v-card-text>
      {{ data.name }}
    </v-card-text>
    <v-card-text>
      <slot />
    </v-card-text>
    <v-card-actions>
      <v-spacer />
      {{ data.price }}
      <v-spacer />
    </v-card-actions>
  </v-card>
</template>
<script>
export default {
  props: {
    data: {
      type: Object,
      required: true
    }
  }
}
</script>
