<template>
  <v-layout
    row
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8

    >
      <div class="text-xs-left">
        <h1>Metadata</h1>
      </div>
      <v-card>
        <v-card-title class="headline">El General</v-card-title>
        <v-card-text>
          <p>Melbourne,Australia</p>
          <p>P: (123) 456-7890</p>
        <Form/>
        </v-card-text>
        <v-card-actions>
          <v-spacer />
        </v-card-actions>
      </v-card>
    </v-flex>
  </v-layout>
</template>
<script>
import Form from '@/components/Form'
export default {
  components: {
    Form
  }
}
</script>
