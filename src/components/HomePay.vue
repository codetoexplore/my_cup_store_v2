<template>
    <v-form class="pa-3">
        <div v-if = "status === ''">
            <div v-if = submitted>
                <p>loading animation</p>
            </div>
            <div v-else>
                <v-text-field
                    label="Card Number"
                    placeholder="5500 0000 0000 0004"
                    required
                    outline
                ></v-text-field>
                <v-text-field
                    label="Expiration Date"
                    placeholder=""
                    required
                    outline
                ></v-text-field>
                <v-text-field
                    label="CVC"
                    placeholder="444"
                    required
                    outline
                ></v-text-field>
            </div>
            <v-btn color="primary">Buy</v-btn>
        </div>
        <div v-else>
            <p>Error</p>
        </div>       

                
        
    </v-form>


</template>

<script>
    export default {
        data () {
            return {
                status: '',
                submitted: false
            }
        }
    }


</script>

<style scoped>

</style>

