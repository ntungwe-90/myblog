<template>
 <div class="card border card1">
        <img :src="post.jetpack_featured_media_url" class="card-img-top" alt="..." />
        <div class="ms-3">
            <p class="text-muted">Front End <small class="text-muted">-1 Month Ago</small></p>
            <h5 class="card-title font-weight-bold">{{ post.title.rendered }}</h5>
            
            <p class="text-muted" v-html="post.excerpt.rendered"></p>
            <div class="d-flex cardflex">
                <p class="card-text"><small class="text-muted"> 3 mins Read</small></p>
                <p class="card-text text-primary"><small>Full Read<svg xmlns="http://www.w3.org/2000/svg" width="16"
                            height="16" fill="currentColor" class="bi bi-arrow-right" viewBox="0 0 16 16">
                            <path fill-rule="evenodd"
                                d="M1 8a.5.5 0 0 1 .5-.5h11.793l-3.147-3.146a.5.5 0 0 1 .708-.708l4 4a.5.5 0 0 1 0 .708l-4 4a.5.5 0 0 1-.708-.708L13.293 8.5H1.5A.5.5 0 0 1 1 8z" />
                        </svg></small></p>
            </div>
        </div>
    </div>

</template>

<script>
export default{
     name: "MoreArticles",
    props: {
        post: {
            type: Number,
            required: true
        }
}}
</script>