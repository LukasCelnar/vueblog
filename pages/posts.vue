<template>
    <div>
        <BlogLogo />
        
        <div v-if="loading" class="text-center my-5">
            <div class="spinner-border" role="status">
                <span class="visually-hidden"></span>
            </div>
        </div>

        <div class="row p-5">
            <div v-for="post in posts" :key="post.id" class="col-md-6">
                <BlogCard :post="post" />
            </div>
        </div>
    </div>
</template>
  
<script>
    import axios from 'axios'

    export default {
        data() {
            return {
                posts: [],
                loading: true,
            }
        },
        async mounted() {
            const response = await axios.get('https://62fe137ba85c52ee482f275b.mockapi.io/api/v1/posts')
            this.posts = response.data
            this.loading = false;
        },
        name: 'PostsPage'
  }
</script>