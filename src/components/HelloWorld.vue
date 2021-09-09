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
            method="POST"
            id="message-form"
            
            
          >
          <v-text-field
              v-model="phone"
              :rules="phoneRule"
              id="phone"
              color="deep-purple"
              label="Phone number"
            ></v-text-field>
          <v-textarea
                outlined
                :rule="messageRule"
                label="Type message here"
                id="text"
                v-model="text"
                placeholder="sms goes here..."
              ></v-textarea>

          <v-btn
            
            color="success"
            class="mr-4"
            @click="sendSms()"
          >
            Send
          </v-btn>

          <v-btn
            color="error"
            class="mr-4"
            @click="reset()"
          >
            Reset Form
          </v-btn>
        </v-form>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>
<script>
import axios from 'axios'
//import qs from 'querystring'
export default {
  data() {
    return {
      phone: '',
      text: '',
      status: '',
      phoneRule: [
        v => !!v || 'Recipient Phone Number Required'
      ],
      messageRule: [
        v => !!v || 'Message Required'
      ]
    }
  },
  methods: {
    reset() {
      this.$refs.form.reset()
    },
    
    sendSms() {
      const url = 'https://dramatic-agreeable-forest.glitch.me/send_text'
      axios.post(url, {
      text: this.text,
      phone: this.phone
      })
        .then(res => {
          console.log(res)
        })
        .catch( err => {
          console.log(err)
        })
    }

  },
  
}
</script>