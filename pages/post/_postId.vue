<template>
  <div class="container my-4">
    <div class="row">
      <div class="col-md-8 offset-md-2">
        <div class="card mb-3">
          <img :src="post.image" class="card-img-top" alt="Post Image">
          <div class="card-body">
            <h5 class="card-title">{{ post.title }}</h5>
            <h6 class="card-subtitle mb-2 text-muted">{{ new Date(post.createdAt).toLocaleDateString() }}</h6>
            <p class="card-text">{{ post.content }}</p>
          </div>
          <div class="card-footer">
            <h6>Comments</h6>
            <hr>
            <Comments />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      post: {},
    }
  },
  async mounted() {
    const postRes = await axios.get(`https://62fe137ba85c52ee482f275b.mockapi.io/api/v1/posts/${this.$route.params.postId}`)
    this.post = postRes.data
  }
}
</script>
