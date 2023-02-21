<template>
  <div>
    <n-space>
      <n-button>
        <input type="file" @change="handleFileUpload" />
      </n-button>
    </n-space>
  </div>
</template>

<script setup lang="ts">
import axios from "axios";
import { ref } from "vue";

const audioFile = ref<File | null>(null);

const handleFileUpload = (event: Event) => {
  const inputElement = event.target as HTMLInputElement;
  if (inputElement.files && inputElement.files.length > 0) {
    audioFile.value = inputElement.files[0];
  }
};

const submitAudio = async () => {
  const formData = new FormData();
  if (audioFile.value) {
    formData.append("audio", audioFile.value);
    try {
      const response = await axios.post("/api/upload-audio", formData);
      console.log(response.data);
    } catch (error) {
      console.log(error);
    }
  }
};
</script>
