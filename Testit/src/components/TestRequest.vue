<template>
  <v-form v-model="valid">
    
      <v-row>
        <v-col cols="5">
          <v-textarea variant="solo" rows="28" />
        </v-col>
        <v-col cols="2" class="action-button">
          <v-btn color="blue-lighten-1" variant="outlined" text="Write Test" />
        </v-col>
        <v-col cols="5">
          <v-btn color="green-lighten-1" variant="outlined" text="Copy" class="copy-btn"/>
          <v-textarea class="textarea-field" variant="solo" rows="28" />
        </v-col>
      </v-row>

   
  </v-form>
</template>
<script setup lang="ts">
import { ref } from 'vue';

const valid = ref<boolean>();
</script>
<style lang="scss" scoped>
.copy-btn {
  z-index: 10;
  margin: 10px 0 0 10px;
  position: fixed;
}

.textarea-field {
  z-index: 1;
}

.action-button {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>