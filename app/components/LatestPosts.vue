<template>
  <div class="columns is-desktop">
    <a v-for="(post,index) in getPosts" :key="index" :href="'posts/'+post.slug">
      <card class="home-card" :post="post">{{post.excerpt}}</card>
    </a>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import Card from "~/components/Card";
export default {
  name: "LatestPosts",
  data() {
    return {};
  },
  components: {
    Card
  },
  computed: {
    getPosts() {
      return this.$store.state.posts.list;
    }
  }
};
</script>

<style>
.card {
  transition: 0.4s;
}
.card:hover {
  -ms-filter: "progid:DXImageTransform.Microsoft.Shadow(Strength=5, Direction=135, Color=#000000)"; /*IE 8*/
  -moz-box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2); /*FF 3.5+*/
  -webkit-box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2); /*Saf3-4, Chrome, iOS 4.0.2-4.2, Android 2.3+*/
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2); /* FF3.5+, Opera 9+, Saf1+, Chrome, IE10 */
  filter: progid:DXImageTransform.Microsoft.Shadow(Strength=5, Direction=135, Color=#000000); /*IE 5.5-7*/
}
.card img {
  min-height: 250px;
}
.card h3 {
  font-weight: bold;
}
.card .button {
  display: block;
  margin: 20px 0 0 0;
}
.card-content {
  padding: 0;
}
</style>
