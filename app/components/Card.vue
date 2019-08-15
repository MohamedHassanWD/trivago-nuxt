<template>
  <div class="column">
    <div class="card">
      <div class="card-header">
        <h3>{{post.card_title}}</h3>
      </div>
      <div class="card-content">
        <div class="content has-text-centered">
          <img :src="this.post.thumbnail_url" alt />
        </div>
      </div>
      <footer class="card-footer">
        <div class="card-footer-item">
          <span>
            <slot />
          </span>
        </div>
      </footer>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      required: true
    }
  }
};
</script>

<style>
.card-header {
  padding: 15px;
}
</style>
