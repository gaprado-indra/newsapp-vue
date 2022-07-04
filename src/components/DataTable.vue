<template>

    <div v-if="news && news.length" class="data-table-container">
        <div v-for="post of news" :key="post" class="individual-news">
            <div class="news-image-container">
                <img alt="news logo" src="post.urlToImage" />
            </div>
            <div class="news-details-container">
                <p>{{post.title}}</p>
                <p>{{post.author}}</p>
                <p>{{post.url}}</p>
                <a href="post.url"><button>GO TO PAGE</button></a>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

    export default {
        name: "DataTable",
        data() {
            return {
            news: [],
            errors: []
            }
        },

        // Fetches news when the component is created.
        created() {
            axios.get(`https://newsapi.org/v2/everything?domains=wsj.com&apiKey=d2e5c70185754ff0aa63e3d65fc5163a`)
            .then(response => {
            // JSON responses are automatically parsed.
            this.news = response.data.articles
            console.log(response)
            })
            .catch(e => {
            this.errors.push(e)
            })
        }
    };
</script>