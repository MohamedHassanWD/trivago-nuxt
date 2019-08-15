<template>
  <section>
    <section class="hero is-fullheight is-medium">
      <div class="hero-body">
        <div class="hero-text">
          <h2>Florida Vacations: Start Planning Your Trip for an Escape to the Sunshine State</h2>
          <a
            href="https://magazine.trivago.com/florida-vacations/"
            class="button is-primary is-medium"
          >Read More</a>
        </div>
      </div>
    </section>
    <div class="section">
      <div class="row">
        <h2>Latest Posts</h2>
        <LatestPosts />
      </div>
      <div class="columns is-desktop">
        <div class="column">
          <div id="searched-tags">
            <h2>Most searched tags</h2>
            <Tags :tags="tags" />
          </div>
        </div>
      </div>
    </div>
    <Subscribe />
  </section>
</template>

<script>
import Card from "~/components/Card";
import LatestPosts from "~/components/LatestPosts";
import Tags from "~/components/Tags";
import Subscribe from "~/components/Subscribe";

export default {
  name: "HomePage",
  data() {
    return {
      tags: [
        {
          text: "The Pyramids Egypt",
          slug: "the-pyramids-egypt"
        },
        {
          text: "International Flights",
          slug: "international-flights"
        },
        {
          text: "Miami Florida",
          slug: "miami-florida"
        },
        {
          text: "Adult Only Resorts",
          slug: "adult-only-resorts"
        },
        {
          text: "Mexico & the South Coast",
          slug: "mexico-and-the-south-coast"
        },
        {
          text: "Southern Cali",
          slug: "southern-cali"
        },
        {
          text: "Europe",
          slug: "europe"
        }
      ]
    };
  },
  components: {
    Card,
    LatestPosts,
    Tags,
    Subscribe
  },
  head() {
    return {
      title: "Trivago Magazine",
      meta: [
        {
          hid: "description",
          name: "description",
          content:
            "Magazine showcases the most compelling hotel experiences - Find out the secrets behind your next room, as well as tips about when and where to go!"
        },
        {
          hid: "og:title",
          name: "og:title",
          content: "Trivago Magazine: hotel inspiration from trivago.com"
        },
        {
          hid: "og:description",
          name: "og:description",
          content:
            "Magazine showcases the most compelling hotel experiences - Find out the secrets behind your next room, as well as tips about when and where to go!"
        },
        {
          hid: "og:image",
          name: "og:image",
          content:
            "https://imgcy.trivago.com/c_lfill,f_auto,g_faces,h_480,q_auto:good,w_715/mag/2018/10/10160708/magazine-placeholder.jpg"
        },
        {
          hid: "twitter:card",
          name: "twitter:card",
          content: "summary"
        },
        {
          hid: "twitter:title",
          name: "twitter:title",
          content: "Trivago Magazine: hotel inspiration from trivago.com"
        },
        {
          hid: "twitter:description",
          name: "twitter:description",
          content:
            "Trivago Magazine showcases the most compelling hotel experiences - Find out the secrets behind your next room, as well as tips about when and where to go!"
        },
        {
          hid: "twitter:image",
          name: "twitter:image",
          content:
            "https://imgcy.trivago.com/c_lfill,f_auto,g_faces,h_480,q_auto:good,w_715/mag/2018/10/10160708/magazine-placeholder.jpg"
        }
      ]
    };
  }
};
</script>

<style scoped>
h2 {
  font-size: 2rem;
  margin: 0 0 30px 0;
}
.hero {
  background-image: url("../assets/florida-vacations-alex-shutin-umlyv-9gr0-unsplash.jpg");
  background-size: cover;
  background-position: center;
  display: flex;
  justify-content: flex-end;
}
.hero-text {
  width: 100%;
  background: rgba(0, 0, 0, 0.3);
  text-align: center;
  color: #fff;
  padding: 20px;
}
#searched-tags {
  margin: 40px 10px;
  padding: 40px 0;
}
</style>
