<template>
    <div>
        <div v-for="comment in comments" :key="comment.id" class="media mb-3">
            <img v-bind:src="comment.avatar" class="mr-3" width="50" alt="Comment user image">
            <div class="media-body">
                <h5 class="mt-0">{{ comment.name }}</h5>
                <h6 class="card-subtitle mb-2 text-muted">{{ new Date(comment.createdAt).toLocaleDateString() }}</h6>
                <p>{{ comment.comment }}</p>
            </div>
        </div>
    </div>
    
</template>

<script>
    import axios from 'axios'
    export default {
        data() {
            return {
                comments: [],
            }
        },
        async mounted() {
            const commentsRes = await axios.get(`https://62fe137ba85c52ee482f275b.mockapi.io/api/v1/comments`)
            this.comments = commentsRes.data
        },
    }

</script>