<template>
  <v-form>
    <v-container>
      <v-layout>
        <v-flex>
          <v-text-field
            label="Paste Your Link Here"
            placeholder="https://twitter.com/tweetsoncup/status/1133066554000777216"
          ></v-text-field>
          <v-btn @click="submit" color="primary">Continue</v-btn>
        </v-flex>
      </v-layout>
    </v-container>
  </v-form>
</template>

<script>
export default {};
</script>

<style scoped></style>
