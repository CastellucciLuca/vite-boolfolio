<template>
    <article class="single-post card p-3 mb-3">
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
</template>
<script>
export default {
    name: 'AppPost',
        
    data() {
        return {
            
        }
    },
    props:
        {
            'post': {
                type: Object,
                required: true,
            },
    }
}
</script>
<style lang="">
    
</style>