<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <v-card ref="form" class="pa-md-4 mx-lg-auto">
          <v-card-title>Send To</v-card-title>
          <v-card-text>
            <v-row>
              <v-col cols="4">
                <v-text-field label="to" />
                <v-text-field label="cc" />
                <v-text-field label="bcc" />
                <v-text-field label="from" />
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="12">
                <v-textarea label="Message" />
                <v-input
                  :messages="['Messages']"
                  append-icon="mdi-window-close"
                  prepend-icon="mdi-file"
                >
                  Default Slot
                </v-input>
              </v-col>
            </v-row>
          </v-card-text>
          <v-card-actions class="text-center">
            <v-spacer />
            <v-btn class="ma-2" tile color="indigo" dark to="/feature/invoice/">
              Submit
            </v-btn>
            <v-spacer />
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>
<style>
  #input-usage .v-input__prepend-outer,
  #input-usage .v-input__append-outer,
  #input-usage .v-input__slot,
  #input-usage .v-messages {
    border: 1px dashed rgba(0,0,0, .4);
  }
</style>
