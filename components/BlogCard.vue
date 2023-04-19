<template>
    <b-card no-body class="overflow-hidden mx-auto mt-3" style="max-width: 700px;">
        <b-row no-gutters>
            <b-col md="6">
            <b-card-img :src="post.image" alt="Image" class="rounded-0"></b-card-img>
            </b-col>
            <b-col md="6">
            <b-card-body :title="post.title">
                <h6 class="card-subtitle mb-2 text-muted">{{ new Date(post.createdAt).toLocaleDateString() }}</h6>
                <b-card-text>
                {{ post.content.length > 175 ? `${post.content.slice(0, 175)}...` : post.content  }}
                </b-card-text>
                <div class="d-flex justify-content-end h-100">
                    <b-button class="mt-auto" @click="redirectToPost">Read More</b-button>
                </div>
            </b-card-body>
            </b-col>
        </b-row>
    </b-card>

</template>

<script>
    export default {
        name: 'BlogCardComponent',
        props: ['post'],
        methods: {
            redirectToPost() {
                this.$router.push(`/post/${this.post.id}`)
            }
        }   
    }
</script>