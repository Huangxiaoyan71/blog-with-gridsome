<template>
  <Layout>
    <!-- Page Header-->
    <header class="masthead" style="background-image: url('/img/home-bg.jpg')">
        <div class="container position-relative px-4 px-lg-5">
            <div class="row gx-4 gx-lg-5 justify-content-center">
                <div class="col-md-10 col-lg-8 col-xl-7">
                    <div class="site-heading">
                        <h1>Clean Blog</h1>
                        <span class="subheading">A Blog Theme by Start Bootstrap</span>
                    </div>
                </div>
            </div>
        </div>
    </header>

    <!-- Main Content-->
    <div class="container px-4 px-lg-5">
        <div class="row gx-4 gx-lg-5 justify-content-center">
            <div class="col-md-10 col-lg-8 col-xl-7">
                <!-- Post preview-->
                <div
                    class="post-preview"
                    v-for="edge in $page.posts.edges"
                    :key="edge.node.id"
                >
                    <g-link :to="`/post/${edge.node.id}`">
                        <h2 class="post-title">{{ edge.node.title }}</h2>
                        <h3 class="post-subtitle">{{ edge.node.content }}</h3>
                    </g-link>
                    <p class="post-meta">
                        Posted by
                        <a href="#!">{{ edge.node.auths ? edge.node.auths.last_name : ''}}</a>
                        on {{ edge.node.created_at }}
                    </p>
                    <hr class="my-4" />
                </div>
                <!-- Pager-->
                <div class="d-flex justify-content-end mb-4"><a class="btn btn-primary text-uppercase" href="#!">Older Posts →</a></div>
            </div>
        </div>
    </div>
  </Layout>
</template>

<page-query>
    query {
        posts: allStrapiPost {
            edges {
                node {
                    id
                    title
                    content
                    created_at
                    tags {
                        id
                        title
                    }
                    auths {
                        id
                        first_name
                        last_name
                    }
                }
            }
        }
    }
</page-query>

<script>
export default {
  metaInfo: {
    title: 'Hello, world!'
  },
  name: "HomePage"
}
</script>

<style>
</style>
