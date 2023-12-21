<script>
window.LATEST_ARTICLES =[
    {
        "title": "Find new ways to travel north",
        "publishDate": "2023-06-03T13:51:50.417Z",
        "category": "news",
        "url": "/articles/4738.html"
    },
    {
        "title": "When will it become possible to use timetravel in order to fix your earlier mistakes?",
        "publishDate": "2023-06-01T12:18:10.317Z",
        "category": "essay",
        "url": "/articles/7256.html"
    },
    {
        "title": "10 ways to write better text",
        "publishDate": "2023-06-03T09:00:32.200Z",
        "category": "news",
        "url": "/articles/7247.html"
    },
    {
        "title": "Announcement: we have a new website category",
        "publishDate": "2023-05-30T17:12:13.102Z",
        "category": "news",
        "url": "/articles/1749.html"
    },
    {
        "title": "Weekly news",
        "publishDate": "2023-05-29T00:23:15.276Z",
        "category": "news",
        "url": "/articles/1538.html"
    },
    {
        "title": "In-depth travel guide for Tanzania",
        "publishDate": "2023-05-31T11:12:43.003Z",
        "category": "essay",
        "url": "/articles/2594.html"
    }

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
            const filtered = this.articles.filter(item => {
                return (this.showNews && item.category === 'news') ||
                    (this.showEssay && item.category === 'essay')
            })

            return filtered.sort((a, b) => new Date(b.publishDate) - new Date(a.publishDate));
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
                <li v-for="(article) in filteredArticles" :key="article.title">
                    <a :href="article.url">{{ article.title }} {{ article.publishDate }}</a>
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