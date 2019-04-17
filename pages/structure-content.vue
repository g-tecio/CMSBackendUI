<template>
  <v-container>
    <v-flex xs12 sm12 md12>
      <v-select
        v-on:change="createForm()"
        v-model="selected_metadata"
        :items="metadatas"
        item-text="name"
        label="Select Metadata"
        required
      ></v-select>
    </v-flex>
    <v-flex :key="field" v-for="field in form" md12>
      <v-text-field :type="field.type" v-model="model[field.machine_name]" :label="field.label" required></v-text-field>
    </v-flex>
    <div>
      <v-btn v-on:click="saveContent()" color="info">Success</v-btn>
    </div>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      url:
        "https://0795jhayp2.execute-api.us-east-1.amazonaws.com/Stage/metadata/",
      metadatas: [],
      selected_metadata: "",
      hide_form: true,
      form: [],
      model: {},
      metadata_id: "",
      metadata: {}
    };
  },
  methods: {
    getMetadatas() {
      var config = {
        headers: { "Access-Control-Allow-Origin": "*" }
      };
      this.$axios.get(this.url, config).then(res => {
        this.metadatas = res.data;
      });
    },
    createForm() {
      this.hide_form = false;
      this.metadata = this.metadatas.filter(metadata => {
        return metadata.name.indexOf(this.selected_metadata) > -1;
      });
      this.form = this.metadata[0].attributes;
      this.form.forEach(field => {
        if (field.type == "string") {
          field.type = "text";
        }
        if (field.type == "text") {
          field.type = "textarea";
        }
        if (field.type == "image") {
          field.type = "file";
        }
      });
      console.log(this.form);
    },
    saveContent() {
      var config = {
        headers: { "Access-Control-Allow-Origin": "*" }
      };

      this.form.forEach(field => {
          if (field.type == "number") {
            this.model[field.machine_name] = parseInt(this.model[field.machine_name]);
          }
          
      });
      
      let content = {
        metadata_id: this.metadata[0].id,
        title: "default",
        content: "nothing",
        data: this.model
      };
      console.log(this.model);
      let url_post =
        "http://127.0.0.1:3100/content/addContent";

      this.$axios.post(url_post, content, config).then(res => {
        console.log(res);
      });
    }
  },
  created() {
    this.getMetadatas();
  }
};
</script>
