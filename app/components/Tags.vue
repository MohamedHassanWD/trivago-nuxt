<template>
  <div>
    <b-taglist>
      <b-tag size="is-medium" rounded v-for="(tag,index) in tags" :key="index">{{tag.text}}</b-tag>
    </b-taglist>
  </div>
</template>

<script>
export default {
  name: "Tags",
  props: {
    tags: {
      type: Array,
      required: true
    }
  }
};
</script>

<style scoped>
#searched-tags .tag,
#searched-tags a {
  color: #29343a;
  text-transform: uppercase;
  font-size: 0.8rem;
  transition: 0.3s;
}
#searched-tags .tag:hover {
  -ms-filter: "progid:DXImageTransform.Microsoft.Shadow(Strength=5, Direction=135, Color=#000000)"; /*IE 8*/
  -moz-box-shadow: 0 2px 3px rgba(0, 0, 0, 0.5); /*FF 3.5+*/
  -webkit-box-shadow: 0 2px 3px rgba(0, 0, 0, 0.5); /*Saf3-4, Chrome, iOS 4.0.2-4.2, Android 2.3+*/
  box-shadow: 0 2px 3px rgba(0, 0, 0, 0.5); /* FF3.5+, Opera 9+, Saf1+, Chrome, IE10 */
  filter: progid:DXImageTransform.Microsoft.Shadow(Strength=5, Direction=135, Color=#000000); /*IE 5.5-7*/
}
</style>
