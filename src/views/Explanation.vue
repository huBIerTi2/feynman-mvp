<template>
  <div class="about">
     <v-container fluid>
      <v-layout wrap>
        <v-flex md4>
          <chat-log :explanationUid="explanationId"/>
        </v-flex>
        <v-flex md8>
          <animation :explanationId="explanationId"/>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
import db from '@/database.js'
import ChatLog from '@/components/ChatLog.vue'
import Animation from '@/components/Animation.vue'

export default {
  components: {
    ChatLog,
    Animation
  },
  data() {
    return {
      explanationId: null 
    }
  },
  created() {
    this.explanationId = this.$route.params.id
    this.$root.$on('delete-explanation', this.deleteExplanation)
  },
  watch: {
    $route(to, from) {
      this.explanationId = this.$route.params.id
    }
  },
  methods: {
    deleteExplanation() {
      db.collection('explanations').doc(this.explanationId).delete()
    }
  }
}
</script>
