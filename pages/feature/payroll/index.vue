<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <StaffCRUD />
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
import StaffCRUD from '@/components/StaffCRUD'
export default {
  components: {
    StaffCRUD
  }
}
</script>
