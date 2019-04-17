<template>
  <v-form black ref="form" v-model="valid" lazy-validation color="white">
    <v-container>
      <v-layout row wrap>
        <v-flex xs12 sm6 md3>
          <h3>Name</h3>
        </v-flex>

        <v-text-field v-model="name" label="Name" required></v-text-field>

        <v-flex xs12 sm6 md3></v-flex>
        <v-flex xs12 sm6 md3></v-flex>
      </v-layout>
    </v-container>

    <v-container>
      <v-layout row wrap :key="field" v-for="(field, key) in fields">
        <v-flex xs12 sm6 md3></v-flex>
        <v-flex xs12 sm6 md3>
          <v-text-field v-model="fields[key].label" label="Label" required></v-text-field>
        </v-flex>

        <v-flex xs12 sm6 md3>
          <v-text-field v-model="fields[key].machine_name" label="Machine Name" required></v-text-field>
        </v-flex>

        <v-flex xs12 sm6 md3>
          <v-select v-model="fields[key].type" :items="types" label="Type" required></v-select>
        </v-flex>
      </v-layout>
      <v-layout row wrap>
        <v-flex xs12 sm6 md3></v-flex>

        <!-- <v-flex xs12 sm6 md3>
          <v-select v-model="select" :items="items" label="Required" required></v-select>
        </v-flex>-->

        <!-- <v-flex xs12 sm6 md3>
          <v-text-field v-model="label" label="Min-Length" required></v-text-field>
        </v-flex>

        <v-flex xs12 sm6 md3>
          <v-text-field v-model="label" label="Max-Length" required></v-text-field>
        </v-flex>-->
        <v-flex xs12 sm6 md3>
          <v-btn v-on:click="addField()" icon color="red" class="white--text">
            <v-icon>add</v-icon>
          </v-btn>
        </v-flex>

        <v-flex xs12 sm6 md3></v-flex>
        <v-flex xs12 sm6 md3></v-flex>

        <v-flex xs12 sm6 md3>
          <v-btn v-on:click="saveMetadata()" class="deep-purple darken-1 white--text">Submit</v-btn>
        </v-flex>
      </v-layout>
    </v-container>
  </v-form>
</template>

<script>
export default {
  data() {
    return {
      valid: true,
      select: null,
      fields: [{ label: "", machine_name: "", type: "" }],
      types: ["string", "number", "image", "text"],
      name: ""
    };
  },
  methods: {
    addField() {
      this.fields.push({ label: "", machine_name: "", type: "" });
    },
    created() {
      this.addField();
    },
    saveMetadata() {
      let url = 'https://0795jhayp2.execute-api.us-east-1.amazonaws.com/Stage/metadata/addMetadata';
      let metadata = {
        name: this.name,
        attributes: this.fields,
        owner_id: "pwAs7k58aSd"
      }
      this.$axios.post(url, metadata).then(res => {
        console.log(res);
      })
      
    }
  }
};
</script>

<style>
</style>
