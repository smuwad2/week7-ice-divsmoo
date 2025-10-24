<script>
import axios from 'axios';

export default {
  data() {
    return {
      subject: '',
      entry: '',
      selMood: 'Angry' 
    };
  },

  computed: {
    baseUrl() {
      if (window.location.hostname === 'localhost') {
        return 'http://localhost:3000';
      } else {
        const codespace_host = window.location.hostname.replace('5173', '3000');
        return `https://${codespace_host}`;
      }
    }
  },

  methods: {
    addPost() {
      axios.get(`${this.baseUrl}/addPost`, {
        params: {
          subject: this.subject,
          entry: this.entry,
          mood: this.selMood
        }
      }).catch(err => {
        console.error('addPost error', err);
      });
    }
  }
};
</script>

<template>
  <div class="table m-2">
    <h3>Add a New Blog Post</h3>

    Subject:
    <input type="text" size="30" v-model="subject" required />
    <br />

    Entry:
    <br />
    <textarea name="entry" cols="80" rows="5" v-model="entry" required></textarea>
    <br />

    Mood:
    <select v-model="selMood">
      
      <option value="Angry">Angry</option>
      <option value="Sad">Sad</option>
      <option value="Happy">Happy</option>
      <option value="Neutral">Neutral</option>
    </select>
    <br /><br />

   
    <button @click="addPost">Submit New Post</button>

    <hr />
    Click <router-link to="/ViewPosts/">here</router-link> to return to Main Page
  </div>
</template>
