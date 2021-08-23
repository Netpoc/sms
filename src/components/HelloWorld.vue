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
            lazy-validation
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
                id="message"
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
      message: '',
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
      const url = 'https://lazersms.com/api/send/'
      
      axios.post(url, { useCredentails: true }, {
        'to': this.phone,
        'message': this.message,
        'from': +17202592794,
        'apikey': 'd995b6a62d817ca097ae7b3e157520f26e9711a11bedabb3df5c56d5ff3ecd9c',
      })
        .then(res => {
          this.status = res.data
        })
        .catch( err => {
          this.status = err
        })
    }

  },
  
}
</script>