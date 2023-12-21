<script>
window.LATEST_ARTICLES =[
    {
        "title": "Find new ways to travel north",
        "publishDate": "2023-12-20T13:51:50.417Z",
        "category": "news",
        "url": "/articles/4738.html"
    },
    {
        "title": "In-depth travel guide for Tanzania",
        "publishDate": "2023-12-16T11:12:43.003Z",
        "category": "essay",
        "url": "/articles/2594.html"
    },
    {
        "title": "10 ways to write better text",
        "publishDate": "2023-12-17T09:00:32.200Z",
        "category": "news",
        "url": "/articles/7247.html"
    },
    {
        "title": "Announcement: we have a new website category",
        "publishDate": "2023-12-17T17:12:13.102Z",
        "category": "news",
        "url": "/articles/1749.html"
    },
    {
        "title": "Weekly news",
        "publishDate": "2023-12-18T00:23:15.276Z",
        "category": "news",
        "url": "/articles/1538.html"
    },
    {
        "title": "News News News",
        "publishDate": "2023-12-20T09:00:32.200Z",
        "category": "news",
        "url": "/articles/7247.html"
    },
    {
        "title": "Outdated",
        "publishDate": "2023-12-10T09:00:32.200Z",
        "category": "essay",
        "url": "/articles/7232.html"
    },
    {
        "title": "When will it become possible to use time travel in order to fix your earlier mistakes?",
        "publishDate": "2023-12-20T12:18:10.317Z",
        "category": "essay",
        "url": "/articles/7256.html"
    },
    {
        "title": "Test article",
        "publishDate": "2023-12-20T12:18:10.317Z",
        "category": "test",
        "url": "/articles/7156.html"
    },
    {
        "title": "Essay Essay Essay",
        "publishDate": "2023-12-19T11:12:43.003Z",
        "category": "essay",
        "url": "/articles/2594.html"
    },

];

export default {
    data() {
        return {
            articles: window.LATEST_ARTICLES,
            showNews: true,
            showEssay: true
        }
    },
    computed: {
        filteredArticles() {
            const currentDate = new Date();
            currentDate.setDate(currentDate.getDate() - 7); 

            const filtered = this.articles.filter(item => {
                const itemDate = new Date(item.publishDate);
                return ((this.showNews && item.category === 'news') ||
                    (this.showEssay && item.category === 'essay')) &&
                    (itemDate >= currentDate);
            })

            return filtered.sort((a, b) => new Date(b.publishDate) - new Date(a.publishDate));
        }
    },
    methods: {
        formatDate(date) {
            const options = { 
                month: 'long', 
                day: 'numeric', 
            };

            return new Date(date).toLocaleDateString('en-US', options);
        }
    }
}

</script>

<template>
    <div class="wrapper">
        <h2>Latest Updates</h2>
        <div class="pagesList">
            <label><input type="checkbox" v-model="showNews">News</label>
            <label><input type="checkbox" v-model="showEssay">Essay</label>
            <ul>
                <li v-for="(article) in filteredArticles.slice(0, 5)" :key="article.title">
                    <a :href="article.url">{{ article.title }} {{ formatDate(article.publishDate) }}</a>
                </li>
            </ul>
        </div>
    </div>
</template>

<style scoped>
    .wrapper {
        margin: 30px
    }
    .pagesList {
        width: clamp(100px, 100%, 500px);
        border: 1px solid black;
        padding: 10px;

        label {
            padding-left: 10px;
        }

        span {
            opacity: 0.5;
        }
    }
</style>