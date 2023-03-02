<template>
    <div class='container'>
        <div class='row'>
            <div class='col-12'>
                <h2>Posts:</h2>
            </div>
            <article class="col-6 single-post card mb-3 p-3" v-for="post in posts">
                    <h6 class="card-header">
                        {{ post.type.name }} --- {{ post.author }}
                    </h6>
                    <img :src="post.image" class="card-img-top" alt="...">
                    <div class="card-body">
                        <h5 class="card-title">{{ post.title }}</h5>
                        <p>
                            <span class="little-technlogy me-3" v-for="technology in post.technologies">
                                #{{ technology.name }}
                            </span>
                        </p>
                        <h6 class="card-subtitle">{{ post.post_date }}</h6>
                        <p class="card-text">{{ post.content.substr(0,250)}}...</p>
                        <a href="#" class="btn btn-primary">Read More...</a>
                    </div>
            </article>
        </div>
    </div>
</template>
<script>
import axios from 'axios';
export default {
    name: 'AppMain',
    data() {
        return {
            posts : [],
            urlAddress: 'http://127.0.0.1:8000/api/posts',
        }
    },
    methods: {
    getPosts() {
        axios.get(this.urlAddress, {
        params: {}
        })
        .then((response) => {
            this.posts= response.data.results.data;
        })
        .catch(function (error) {
            console.warn(error);
        })
    }
    },
    created() {
        this.getPosts();
    },
}
</script>
<style lang="scss" scoped>

</style>