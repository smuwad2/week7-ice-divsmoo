<script>
export default {

    // add code here
    computed: {
        baseUrl() {
            if (window.location.hostname == 'localhost') //when running on vscode
                return 'http://localhost:3000'
            else {
                const codespace_host = window.location.hostname.replace('5173', '3000') //when running on codespace
                return `https://${codespace_host}`;
            }
        }
    },
    methods: {
        addPost(){
            axios.get(`${this.baseUrl}/addPost`,{ //ur telling vue engine to evaluate of baseUrl and will be replaced with its actual value 
                params: {
                    'subject': this.subject,
                    'entry': this.entry,
                    'mood': this.selMood
                }
            })
        }
    }

}
</script>

<template>
    <div class="table m-2">
        <h3>Add a New Blog Post</h3>

        Subject: <input type='text' size='30' v-model='subject' required>
        <br>

        Entry: <br>
        <textarea name='entry' cols='80' rows='5' v-model='entry' required></textarea>
        <br>

        Mood:
        <!-- TODO: Build a dropdown list here for selecting the mood -->

        <br>

        <br>
        <button>Submit New Post</button>

        <hr> Click <a><router-link to="/ViewPosts/">here</router-link></a> to return to Main Page

    </div>
</template>
