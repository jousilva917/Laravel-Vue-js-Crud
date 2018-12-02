<template id="post">
    <div>
        <div class="card" style="width: 18rem;">
            <div class="card-body">
                <h5 class="card-title">Title: {{ post.title }}</h5>
                <p class="card-text">Body: {{ post.body }}</p>
            </div>
        </div>
        <span class="glyphicon glyphicon-arrow-left"></span>
        <router-link v-bind:to="'/'"><i class="fas fa-chevron-left"></i> Voltar para a Home</router-link>
    </div>
</template>
<script>
   export default {
   data: function () {
   return {post: {title: '', body: ''}}
 },
 created: function(){
   let uri = 'http://127.0.0.1:8000/posts/'+this.$route.params.id;
     Axios.get(uri).then((response) => {
     this.post = response.data;
   });
 }
 }
</script>
