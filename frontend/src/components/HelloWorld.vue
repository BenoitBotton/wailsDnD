<script setup lang="ts">
import { ref, onMounted } from 'vue'
import { Events } from "@wailsio/runtime";
import { GreetService } from "../../bindings/changeme";


const name = ref('')
const result = ref('Please enter your name below 👇')
const time = ref('Listening for Time event...')

onMounted(() => {
  Events.On('time', (timeValue: { data: string }) => {
    time.value = timeValue.data;
  });
})

</script>

<template>
  <div id="upload" class="drop-zone" data-file-drop-target>
    Drop files here
  </div>
</template>

<style scoped>
.drop-zone {
    border: 2px dashed #ccc;
    padding: 40px;
    text-align: center;
    transition: all 0.2s ease;
}

.drop-zone.file-drop-target-active {
    border-color: #007bff;
    background-color: rgba(0, 123, 255, 0.1);
}
</style>