<template>
  <v-dialog v-model="dialog">
    <v-btn slot="activator" class="pink darken-1">
      <span class="mr-2 white--text">Save explanation</span>
    </v-btn>
    <v-card>
      <v-card-title class="headline">New Explanation</v-card-title>

      <v-card-text>
        <v-input>
        <input placeholder="Type here..." :value="explanationTitle" @input="$emit('input', $event.target.value)">
      </v-input>
        To save the interaction, enter a title above...
      </v-card-text>

      <v-card-actions>
        <v-spacer></v-spacer>

        <v-btn
          color="green darken-1"
          flat="flat"
          @click="dialog = false"
        >
          Cancel
        </v-btn>

        <v-btn
          color="green darken-1"
          flat="flat"
          @click="handleSave()"
        >
          Save
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  props: ['explanationTitle'],
  methods: {
    handleSave() {
      this.dialog = false 
      this.$emit('pre-save-explanation')
    }
  },
  data() {
    return {
      dialog: false
    }
  }
}
</script>
