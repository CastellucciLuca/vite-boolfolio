<template lang="">
    <div class="row">
        <div class="col-12">
            <h2>
                Posts:
            </h2>
        </div>
    </div>
<div class="row justify-content-around">
    <AppPost  v-for="post in posts" :post="post" class="col-4"/>
</div>
</template>
<script>
import AppPost from '../components/AppPost.vue';
import axios from 'axios';
export default {
    name:'PostsList',
    components:{
        AppPost,
    },
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
            console.log(this.posts);
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
<style lang="">
    
</style>