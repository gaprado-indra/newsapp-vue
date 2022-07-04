<template>
    <div v-if="news && news.length" class="data-table-container">
        <div class="data-table-totalresults">
            <p>{{totalResult}} News Result(s)</p>
        </div>
        <div v-for="post of news" :key="post" class="individual-news">
            <div class="news-image-container">
                <img alt="news logo" :src="post.urlToImage" />
            </div>
            <div class="news-details-container">
                <p>{{post.title}}</p>
                <p>{{post.author}}</p>
                <p>{{post.description}}</p>
                <a :href="post.url"><button>GO TO PAGE</button></a>
            </div>
            <div class="news-detail-publisheddate">
                <p>Published at: {{moment(post.publishedAt).format('YYYY-MM-DD hh:mm')}}</p>
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
            totalResult: 0,
            errors: []
            }
        },

        // Fetches news when the component is created.
        created() {
            axios.get(`https://newsapi.org/v2/top-headlines?country=us&apiKey=d2e5c70185754ff0aa63e3d65fc5163a`)
            .then(response => {
            // JSON responses are automatically parsed.
            this.news = response.data.articles
            this.totalResult = response.data.totalResults
            console.log(response)
            })
            .catch(e => {
            this.errors.push(e)
            })
        }
    };
</script>