<template>
  <Layout>
    <!-- Page Header -->
    <header
      class="masthead"
      :style="
        $page.post.cover
          ? `background-image: url('http://localhost:1337${
              $page.post.cover.url
            }')`
          : ''
      "
    >
      <div class="overlay"></div>
      <div class="container">
        <div class="row">
          <div class="col-lg-8 col-md-10 mx-auto">
            <div class="post-heading">
              <h1>{{ $page.post.title }}</h1>
              <h2 class="subheading">
                <!-- Problems look mighty small from 150 miles up -->
              </h2>
              <span v-if="$page.post.author" class="meta"
                >Posted by
                <a href="#"
                  >{{ $page.post.author.firstname }}
                  {{ $page.post.author.lastname }}</a
                >
                on {{ $page.post.created_at }}</span
              >
            </div>
          </div>
        </div>
      </div>
    </header>

    <!-- Post Content -->
    <article>
      <div class="container">
        <div class="row">
          <div
            class="col-lg-8 col-md-10 mx-auto"
            v-html="mdToHtml($page.post.content)"
          ></div>
        </div>
      </div>
    </article>
  </Layout>
</template>

<page-query>
query ($id: ID!) {
  post: strapiPost (id: $id) {
    id,
    title,
    content,
    created_at,
    cover {
      url
    },
    tags {
      id,
      title
    },
    author {
      id,
      firstname,
      lastname
    }
  }
}
</page-query>

<script>
import MarkdownIt from 'markdown-it'

const md = new MarkdownIt()

export default {
  name: 'PostPage',

  metaInfo({ $page }) {
    return {
      title: $page.post.title
    }
  },

  methods: {
    mdToHtml(str) {
      return str ? md.render(str) : ''
    }
  }
}
</script>
