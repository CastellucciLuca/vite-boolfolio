<template>
    <div class="row">
        <AppPost :post="post" />
    </div>
</template>
<script>
import AppPost from '../components/AppPost.vue';
import axios from 'axios';
export default {
    name: 'SinglePost',
    components: {
        AppPost
    },
    data() {
        return {
            post: [],
            urlAddress: 'http://127.0.0.1:8000/api/posts/' + this.$route.params.id,
        }
    },
    methods: {
        getPost(){
            axios.get(this.urlAddress, {
                params: {
                }
            })
            .then((response) => {
                this.post = response.data.results;
                console.warn(response);
            })
            .catch(function (error) {
                console.warn(error);
            });
        }
    },
    created() {
        this.getPost();
    },
}
</script>
<style lang="">
</style>