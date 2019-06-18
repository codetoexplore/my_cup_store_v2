<template>

  <div class='credit-card-inputs' :class='{ complete }'>
    <card-number class='stripe-element card-number'
      ref='cardNumber'
      :stripe='stripe'
      :options='options'
      @change='number = $event.complete'
    />
    <card-expiry class='stripe-element card-expiry'
      ref='cardExpiry'
      :stripe='stripe'
      :options='options'
      @change='expiry = $event.complete'
    />
    <card-cvc class='stripe-element card-cvc'
      ref='cardCvc'
      :stripe='stripe'
      :options='options'
      @change='cvc = $event.complete'
    />
  </div>

    <!-- <v-form class="pa-3" @submit.prevent >


        <div v-if = "status === ''">
            <div v-if = submitted>
                <p>loading animation</p>
            </div>
            <div v-else>
                <v-text-field
                    label="Card Number"
                    placeholder="5500 0000 0000 0004"
                    class="stripe-element card-number field"
                    ref="cardNumber"
                    :stripe="stripeKey"
                    required
                    outline
                ></v-text-field>
                <v-text-field
                    label="Expiration Date"
                    class="stripe-element card-expiry field"
                    ref="cardExpiry"
                    :stripe="stripeKey"
                    placeholder="MM/YY"
                    required
                    outline
                ></v-text-field>
                <v-text-field
                    label="CVC"
                    class="stripe-element card-cvc field"
                    ref="cardCvc"
                    :stripe="stripeKey"
                    placeholder="444"
                    required
                    outline
                ></v-text-field>
            </div>
            <div v-else-if = "status === 'success'">
                <p>success animation</p>
            </div> 
            <div class="text-xs-center">
                <v-btn color="primary" @click="pay">Buy {{ 1700 | dollar }}</v-btn>
            </div>
        </div>
        <div v-else>
            <p>Error</p>
        </div> 
     

                    
    </v-form> -->


</template>

<script>
import { CardNumber, CardExpiry, CardCvc } from 'vue-stripe-elements-plus'

export default {
  props: [ 'stripe', 'options' ],
  data () {
    return {
      complete: false,
      number: false,
      expiry: false,
      stripeKey: process.env.VUE_APP_MYSTRIPEKEY,
      cvc: false
    }
  },
  components: { CardNumber, CardExpiry, CardCvc },
  methods: {
    update () {
      this.complete = this.number && this.expiry && this.cvc

      // field completed, find field to focus next
      if (this.number) {
        if (!this.expiry) {
          this.$refs.cardExpiry.focus()
        } else if (!this.cvc) {
          this.$refs.cardCvc.focus()
        }
      } else if (this.expiry) {
        if (!this.cvc) {
          this.$refs.cardCvc.focus()
        } else if (!this.number) {
          this.$refs.cardNumber.focus()
        }
      }
      // no focus magic for the CVC field as it gets complete with three
      // numbers, but can also have four
    }
  },
  watch: {
    number () { this.update() },
    expiry () { this.update() },
    cvc () { this.update() }
  }
}
    // import {
    //     CardNumber,
    //     CardExpiry,
    //     CardCvc,
    //     createToken
    // } from 'vue-stripe-elements-plus';
    // import axios from 'axios';
    // export default {
    //     components: { CardNumber, CardExpiry, CardCvc},
    //     data () {
    //         return {
    //             response: '',
    //             status: '',
    //             submitted: false,
    //             number: false,
    //             expiry: false,
    //             cvc: false,
    //             token: null,
    //             stripeKey: process.env.VUE_APP_MYSTRIPEKEY,
    //             url: process.env.VUE_APP_URL,
    //             StripeName: '',
    //             StripeAddressLine1: '',
    //             StripeCity: '',
    //             StripeCountry: '',
    //             StripeCounty: '',
    //             StripePostalCode: '',
    //             StripeEmail: '',
    //             metadata: {},
    //         }
    //     },
    //     filters: {
    //         dollar (amount) {
    //             return `$${amount / 100}`
    //         }
    //     },
    //     methods: {
    //         pay() {
    //             JSON.stringify(createToken);
    //             createToken().then(data => {
    //                 console.log('inside funct');
    //                 this.submitted = true;
    //                 console.log(data.token);
    //                 axios
    //                  .post(
    //                     this.url,
    //                     {
    //                         stripeEmail: this.StripeEmail,
    //                         stripeToken: data.token.id,
    //                         stripeAmt: '1700',
    //                         metadata: this.metadata,
    //                         stripeShippingName: this.StripeName,
    //                         stripeShippingAddressLine1: this.StripeAddressLine1,
    //                         shippingAddressstate: this.StripeCounty,
    //                         stripeShippingAddressCity: this.StripeCity,
    //                         stripeShippingAddressCountry: this.StripeCountry
    //                     },
    //                     {
    //                     headers: {
    //                         'Content-Type': 'application/json'
    //                     }
    //                     }
    //                 )
    //                 .then(response => {
    //                     this.status = 'success';
    //                     this.submitted = false;
    //                     this.response = JSON.stringify(response, null, 2);
    //                     console.log(this.response);
    //                 })
    //                 .catch(error => {
    //                     this.status = 'failure';
    //                     this.response = 'Error: ' + JSON.stringify(error, null, 2);
    //                 });
    //             });
    //         }
    //     }
    // }


</script>

<style scoped>

</style>

