<template>
  <Layout>
    <!-- Page Header -->
    <header class="masthead" style="background-image: url('/img/home-bg.jpg')">
      <div class="overlay"></div>
      <div class="container">
        <div class="row">
          <div class="col-lg-8 col-md-10 mx-auto">
            <div class="site-heading">
              <h1>Clean Blog</h1>
              <span class="subheading">A Blog Theme by Start Bootstrap</span>
            </div>
          </div>
        </div>
      </div>
    </header>

    <!-- Main Content -->
    <div class="container">
      <div class="row">
        <div class="col-lg-8 col-md-10 mx-auto">
          <div v-for="edge in $page.posts.edges" :key="edge.node.id">
            <div class="post-preview">
              <a href="post.html">
                <h2 class="post-title">
                  {{ edge.node.title }}
                </h2>
                <h3 class="post-subtitle"></h3>
              </a>
              <p class="post-meta">
                Posted by
                <a href="#"
                  >{{ edge.node.author.firstname }}
                  {{ edge.node.author.lastname }}</a
                >
                on {{ edge.node.created_at }}
              </p>
            </div>
            <hr />
          </div>
          <!-- Pager -->
          <Pager :info="$page.posts.pageInfo" />
          <!-- <div class="clearfix">
            <a class="btn btn-primary float-right" href="#"
              >Older Posts &rarr;</a
            >
          </div> -->
        </div>
      </div>
    </div>
  </Layout>
</template>

<page-query>
query ($page: Int) {
  posts: allStrapiPost (perPage: 2, page: $page) @paginate {
    pageInfo {
      totalPages
      currentPage
    }
    edges {
      node {
        id
        title
        created_at
        tags{
          id
          title
        }
        author {
          id
          firstname
          lastname
        }
      }
    }
  }
}
</page-query>

<script>
import { Pager } from 'gridsome'

export default {
  name: 'HomePage',

  metaInfo: {
    title: '文章列表'
  },

  components: {
    Pager
  }
}
</script>

<style></style>
