<template>
    <div>
      <button @click="playAudio">Play Audio</button>
      <audio ref="audioPlayer" controls></audio>
    </div>
   </template>
   
   <script>
   import axios from 'axios';
   
   export default {
    methods: {
      async playAudio() {
        try {
          const response = await axios.get('http://localhost:8080/api/song/1', { responseType: 'blob' });
          const url = window.URL.createObjectURL(new Blob([response.data]));
          this.$refs.audioPlayer.src = url;
        } catch (error) {
          console.error('Error:', error);
        }
      },
    },
   };
   </script>
   