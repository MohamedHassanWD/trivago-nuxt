<template>
  <div class="section">
    <section class="hero is-medium" :style="'background-image: url('+post.thumbnail_url+')'">
      <div class="hero-body">
        <div class="hero-text">
          <h1>{{post.title}}</h1>
        </div>
      </div>
    </section>
    <section class="post-meta">
      <div class="row">
        <div class="columns">
          <div class="column is-one-fifth" style="text-align:center">
            <h3 style="font-weight:bold">Written By</h3>
            <span class="author-image">
              <img :src="postAuthor.image" alt />
            </span>
            <span class="author-name">{{postAuthor.name}}</span>
            <span class="post-date">On: {{post.date}}</span>
            <div class="s">
              Rating:
              <div id="rateYo"></div>
            </div>
          </div>
          <div class="column">
            <h2>{{post.title}}</h2>
            <div v-for="(content,index) in post.content" :key="index" class="content-section">
              <div v-if="content.type == 'intro_text'" v-html="content.text" class="intro"></div>
              <div v-if="content.type=='excerpt_in_article'" v-html="content.text" class="excerpt"></div>
              <div class="table-of-contents" v-if="content.type=='table_of_contents'">
                <h2>{{content.header}}</h2>
                <ol>
                  <li
                    v-for="(the_hotel,index) in content.table_of_contents"
                    :key="index"
                  >{{the_hotel.hotel_module.name}}</li>
                </ol>
                <hr />
              </div>
            </div>
            <div class="hotel-module" v-for="(hotel,index) in hotels" :key="index">
              <h2>{{hotel.hotel.name}}</h2>
              <div class="row">
                <div class="columns is-desktop">
                  <div class="column">
                    <div class="hotel-slider">
                      <div v-for="(image,iindex) in hotel.gallery" :key="iindex">
                        <div
                          :style="'background-image:url('+image.url+');height: 550px;background-size:cover'"
                          :title="image.title"
                        ></div>
                      </div>
                    </div>
                  </div>
                  <div class="column">
                    <div class="hotel-tags">
                      <h3>Hotel Tags</h3>
                      <b-tag
                        size="is-medium"
                        rounded
                        v-for="(tag,index) in hotel.hotel.tags"
                        :key="index"
                      >
                        <i v-if="tag.icon == 'gym'" class="fa fa-dumbbell"></i>
                        <i v-if="tag.icon == 'pet'" class="fa fa-paw"></i>
                        <i v-if="tag.icon == 'pool'" class="fa fa-swimming-pool"></i>
                        <i v-if="tag.icon == 'restaurant'" class="fa fa-utensils"></i>
                        <i v-if="tag.icon == 'bar'" class="fa fa-beer"></i>
                        <i v-else :class="'fa fa-'+tag.icon"></i>
                        {{tag.tag_name}}
                      </b-tag>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  validate({ params, store }) {
    return store.state.posts.list.some(post => post.slug === params.slug);
  },
  data() {
    return {
      slug: this.$route.params.slug,
      post: {},
      postMeta: {},
      postAuthor: {},
      hotels: [],
      rating: 0
    };
  },
  head() {
    return {
      title: this.post.title,
      meta: [
        {
          name: "description",
          content: this.postMeta.metadesc
        },
        {
          name: "keywords",
          content: this.postMeta.metakeywords
        },
        {
          name: "og:title",
          content: this.postMeta.opengraph_title
        },
        {
          name: "og:image",
          content: this.postMeta.opengraph_image
        },
        {
          name: "og:description",
          content: this.postMeta.opengraph_description
        },
        {
          name: "og:type",
          content: this.postMeta.opengraph_type
        },
        {
          name: "og:url",
          content: this.postMeta.opengraph_url
        },
        {
          name: "og:locale",
          content: this.postMeta.opengraph_locale
        },
        {
          name: "og:site_name",
          content: this.postMeta.opengraph_site_name
        },
        {
          name: "twitter:title",
          content: this.postMeta.twitter_title
        },
        {
          name: "twitter:image",
          content: this.postMeta.twitter_image
        },
        {
          name: "twitter:description",
          content: this.postMeta.twitter_description
        }
      ]
    };
  },
  created() {
    const post = this.$store.state.posts.list.find(
      post => post.slug === this.slug
    );

    if (post) {
      this.post = post;

      this.$axios
        .$get(this.post.uri)
        .then(res => {
          this.post = res;
          this.postMeta = res.seo_meta;
          this.postAuthor = res.author;
          this.hotels = res.content.filter(function(item) {
            return item.type === "hotel_module";
          });
        })
        .catch(err => {
          this.$buefy.toast.open({
            message:
              "Some error happend when loading the page, you'll be redirected to the homepage in seconds.",
            type: "is-danger",
            position: "is-top-right",
            duration: 5000
          });
          setTimeout(() => {
            window.location = "/";
          }, 5000);
        });
    }
  },
  mounted() {
    $(document).ready(function() {
      $(".hotel-slider").bxSlider({
        mode: "fade"
      });

      var $rateYo = $("#rateYo").rateYo({
        rating: 2,
        numStars: 5,
        fullStar: true,
        starWidth: "30px"
      });

      /* set the option `onChange` */
      $rateYo.click(function () {
        alert('Thanks for rating');
      });
    });
  }
};
</script>

<style scoped>
h1 {
  font-size: 30pt;
}
h2 {
  font-size: 24pt;
  margin: 0 0 30px 0;
}
h3 {
  font-size: 22pt;
  margin: 0 0 20px 0;
}
.hero {
  background-size: cover;
  background-position: top;
}
.hero-text {
  width: 100%;
  background: rgba(0, 0, 0, 0.6);
  text-align: center;
  color: #fff;
  padding: 20px;
}
.intro {
  color: #999;
  font-style: italic;
}
.post-meta {
  margin: 20px;
}
.author-image {
  margin: 20px;
  display: block;
}
.author-image img {
  border-radius: 50%;
  width: 48px;
}
.author-name {
  margin: 0 0 20px 0;
  display: block;
}
.content-section {
  margin: 0 0 20px 0;
  line-height: 30px;
  font-size: 14pt;
}
.table-of-contents {
  margin: 20px;
}
.table-of-contents li {
  margin: 20px;
}
.hotel-module {
  margin: 20px 0 60px 0;
}
.hotel-tags .tag {
  margin: 0 20px 10px 0;
}
.tag .icon {
  margin: 0 5px 0 0 !important;
}
</style>
