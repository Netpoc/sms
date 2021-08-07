<template>
  <v-row>
    <v-col
      cols="12"
      sm="6"
      offset-sm="3"
    >
      <v-card>
        <v-card-title class="blue white--text">
          <span class="text-h5">SMS <small>bulk app</small></span>
        </v-card-title>

        <v-card-text>
          <v-form
    ref="form"
    v-model="valid"
    lazy-validation
  >
    <v-file-input
  truncate-length="15"
></v-file-input>

    

    <v-textarea
          outlined
          name="input-7-4"
          
          placeholder="sms goes here..."
        ></v-textarea>

    

    <v-btn
      :disabled="!valid"
      color="success"
      class="mr-4"
      @click="validate"
    >
      Send
    </v-btn>

    <v-btn
      color="error"
      class="mr-4"
      @click="reset"
    >
      Reset Form
    </v-btn>
  </v-form>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>