<template>
  <v-form class="pa-3">
    <v-text-field 
        v-model="name"
        label="Full Name"
        placeholder="Betty Adams"
        required
        outline
    ></v-text-field>
    <v-text-field
      v-model="email"
      v-validate="'required|email'"
      :error-messages="errors.collect('email')"
      label="E-mail"
      placeholder="mymug@gmail.com"
      required
      outline
    ></v-text-field>
    <v-select
        v-model="country"
        :items="countries"
        :error-messages="selectErrors"
        label="Country"
        placeholder="Select"
        required
        outline
        @change="$v.select.$touch()"
        @blur="$v.select.$touch()"
    ></v-select> 

    <v-text-field 
        v-model="city"
        label="City"
        placeholder="Los Angeles"
        required
        outline
    ></v-text-field>
    <v-text-field
        v-model="address"
        label="Address"
        placeholder="185 Berry Street Suite 550"
        required
        outline
    ></v-text-field>
    <div class="usarest" v-if="country === 'United States'">
        <v-text-field
            v-model="state"
            label="State"
            placeholder="California"
            required
            outline
        ></v-text-field>
        <v-text-field
            v-model="zip"
            label="Zip"
            placeholder="90001"
            required
            outline
        ></v-text-field>
    </div>
    <div v-else>
        <v-text-field
            v-model="state"
            label="County"
            placeholder="Berkshire"
            required
            outline
        ></v-text-field>
        <v-text-field
            v-model="zip"
            label="Postcode"
            placeholder="RG301HL"
            required
            outline
        ></v-text-field>
    </div>
    
    

    <v-btn color="primary" @click="submit">Continue</v-btn>
    <v-btn >Go Back</v-btn>
  </v-form>
</template>

<script>
    import Vue from 'vue'
    import VeeValidate from 'vee-validate'

    Vue.use(VeeValidate)

    export default {
        $_veeValidate: {
            validator: 'new'
        },

        data: () => ({
            name: "",
            email: "",
            city: "",
            country: "",
            state: "",
            zip: "",
            address: "",
            
            countries: ["Afghanistan","Albania","Algeria","Andorra","Angola","Anguilla","Antigua &amp; Barbuda","Argentina","Armenia","Aruba","Australia","Austria","Azerbaijan","Bahamas"
                        ,"Bahrain","Bangladesh","Barbados","Belarus","Belgium","Belize","Benin","Bermuda","Bhutan","Bolivia","Bosnia &amp; Herzegovina","Botswana","Brazil","British Virgin Islands"
                        ,"Brunei","Bulgaria","Burkina Faso","Burundi","Cambodia","Cameroon","Canada","Cape Verde","Cayman Islands","Chad","Chile","China","Colombia","Congo","Cook Islands","Costa Rica"
                        ,"Cote D Ivoire","Croatia","Cruise Ship","Cyprus","Czech Republic","Denmark","Djibouti","Dominica","Dominican Republic","Ecuador","Egypt","El Salvador","Equatorial Guinea"
                        ,"Estonia","Ethiopia","Falkland Islands","Faroe Islands","Fiji","Finland","France","French Polynesia","French West Indies","Gabon","Gambia","Georgia","Germany","Ghana"
                        ,"Gibraltar","Greece","Greenland","Grenada","Guam","Guatemala","Guernsey","Guinea","Guinea Bissau","Guyana","Haiti","Honduras","Hong Kong","Hungary","Iceland","India"
                        ,"Indonesia","Iraq","Ireland","Isle of Man","Israel","Italy","Jamaica","Japan","Jersey","Jordan","Kazakhstan","Kenya","Kuwait","Kyrgyz Republic","Laos","Latvia"
                        ,"Lebanon","Lesotho","Liberia","Libya","Liechtenstein","Lithuania","Luxembourg","Macau","Macedonia","Madagascar","Malawi","Malaysia","Maldives","Mali","Malta","Mauritania"
                        ,"Mauritius","Mexico","Moldova","Monaco","Mongolia","Montenegro","Montserrat","Morocco","Mozambique","Namibia","Nepal","Netherlands","Netherlands Antilles","New Caledonia"
                        ,"New Zealand","Nicaragua","Niger","Nigeria","Norway","Oman","Pakistan","Palestine","Panama","Papua New Guinea","Paraguay","Peru","Philippines","Poland","Portugal"
                        ,"Puerto Rico","Qatar","Reunion","Romania","Russia","Rwanda","Saint Pierre &amp; Miquelon","Samoa","San Marino","Satellite","Saudi Arabia","Senegal","Serbia","Seychelles"
                        ,"Sierra Leone","Singapore","Slovakia","Slovenia","South Africa","South Korea","Spain","Sri Lanka","St Kitts &amp; Nevis","St Lucia","St Vincent","St. Lucia","Sudan"
                        ,"Suriname","Swaziland","Sweden","Switzerland","Taiwan","Tajikistan","Tanzania","Thailand","Timor L'Este","Togo","Tonga","Trinidad &amp; Tobago","Tunisia"
                        ,"Turkey","Turkmenistan","Turks &amp; Caicos","Uganda","Ukraine","United Arab Emirates","United Kingdom","United States","United States Minor Outlying Islands","Uruguay"
                        ,"Uzbekistan","Venezuela","Vietnam","Virgin Islands (US)","Yemen","Zambia","Zimbabwe"]
        }),
        dictionary: {
            attributes: {
                email: 'E-mail Address'
          // custom attributes
            },
            custom: {
                name: {
                required: () => 'Name can not be empty'
            // custom messages
            },
            select: {
                required: 'Select field is required'
             }
        },
        mounted () {
            this.$validator.localize('en', this.dictionary);
        },
        methods: {
            submit() {
                this.$validator.validateAll();
            }
        }
    }
    }
    
</script>

<style></style>
