<template id="post-list">
    <div class="row">
        <div class="ml-auto">
        <router-link class="btn btn-xs btn-primary" v-bind:to="{path: '/add-post'}">
        <span><i class="fas fa-plus"></i></span>
        Add new Post
        </router-link>
            <br>
            <br>
        </div>
        <table class="table table-bordered">
            <thead>
                <tr>
                    <th scope="col">#</th>
                    <th scope="col">Post Tilte</th>
                    <th scope="col">Post Body</th>
                    <th scope="col">Created At</th>
                    <th scope="col">Updated At</th>
                    <th scope="col">Actions</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(post, index) in filteredPosts">
                    <td>{{ index + 1 }}</td>
                    <td>{{ post.title }}</td>
                    <td>{{ post.body }}</td>
                    <td>{{ post.created_at }}</td>
                    <td>{{ post.updated_at }}</td>
                    <td>
                    <router-link class="btn btn-info btn-xs" v-bind:to="{name: 'Viewpost', params: {id: post.id}}"><i class="fa fa-eye" aria-hidden="true"></i> Show</router-link>
                    <router-link class="btn btn-warning btn-xs" v-bind:to="{name: 'Editpost', params: {id: post.id}}"><i class="fas fa-pencil-alt" aria-hidden="true"></i> Edit</router-link>
                    <router-link class="btn btn-danger btn-xs" v-bind:to="{name: 'Deletepost', params: {id: post.id}}"><i class="fas fa-trash" aria-hidden="true"></i> Delete</router-link>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>



<script>
export default {
  data:function(){
    return {posts: ''};
  },
  created: function() {
    let uri = 'http://127.0.0.1:8000/posts/';
    Axios.get(uri).then((response) => {
      this.posts = response.data;
    });
  },
  computed: {
    filteredPosts: function(){
      if(this.posts.length) {
        return this.posts;
      }
    }
  }
}
</script>

<style>

</style>
