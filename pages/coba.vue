<template>
  <v-row>
    <v-col v-for="item in hapes" :key="item.id" cols="12" sm="12" md="3">
      <CardContainer :data="item">
        <v-avatar color="red">
          J
        </v-avatar>
      </CardContainer>
    </v-col>
  </v-row>
</template>
<script>
export default {
  data () {
    return {
      hapes: []
    }
  },
  created () {
    this.hapes = [{
      id: 1,
      name: 'Bil bil',
      price: 2000
    }, {
      id: 2,
      name: 'Bil bil',
      price: 3000
    }
    ]
  }
}
</script>
