<template>

  <v-form 
  black
    ref="form"
    v-model="valid"
    lazy-validation
    color="white"
  >
  <v-container>
      <v-layout row wrap>
        <v-flex xs12 sm6 md3>
          <h3>Name</h3>
        </v-flex>
        
    <v-text-field
      v-model="name"
      label="Name"
      required
    ></v-text-field>

<v-flex xs12 sm6 md3>
      </v-flex>
      <v-flex xs12 sm6 md3>
      </v-flex>

     </v-layout>
  </v-container>

  <v-container>
      <v-layout row wrap>
        <v-flex xs12 sm6 md3>
        <h3>Fields</h3> 
        </v-flex>
        <v-flex xs12 sm6 md3>
    <v-text-field
      v-model="label"
      label="Label"
      required
    ></v-text-field>
        </v-flex>

        <v-flex xs12 sm6 md3>
      <v-text-field
      v-model="label"
      label="Machine Name"
      required
    ></v-text-field>
        </v-flex>

        <v-flex xs12 sm6 md3>
    <v-select
      v-model="select"
      :items="items"
      label="Type"
      required
    ></v-select>
        </v-flex>

      <v-flex xs12 sm6 md3>
      </v-flex>

        <v-flex xs12 sm6 md3>
    <v-select
      v-model="select"
      :items="items"
      label="Required"
      required
    ></v-select>
        </v-flex>

        <v-flex xs12 sm6 md3>
          <v-text-field
      v-model="label"
      label="Min-Length"
      required
    ></v-text-field>
        </v-flex>

        <v-flex xs12 sm6 md3>
          <v-text-field
      v-model="label"
      label="Max-Length"
      required
      >
          </v-text-field>
        </v-flex>
      <v-flex xs12 sm6 md3>
  <v-btn icon color="red" class="white--text">
      <v-icon>add </v-icon>
    </v-btn>
      </v-flex>

         <v-flex xs12 sm6 md3>
      </v-flex>
         <v-flex xs12 sm6 md3>
      </v-flex>

      <v-flex xs12 sm6 md3>
    <v-btn 
      
      class="deep-purple darken-1 white--text"
    >
     Submit
    </v-btn>
      </v-flex>

      </v-layout>
  </v-container>
  </v-form>
</template>

<script>
  export default {
    data: () => ({
      valid: true,
      select: null,
      items: [
        'Item 1',
        'Item 2',
        'Item 3',
        'Item 4'
      ],
      checkbox: false
    })
  }
</script>

<style>

</style>
