<template>
  <Layout>

    <div class="container">
      <div class="journal-hero">
        <h1 class="journal-header">
          please go to strapi set conetent...
        </h1>
      </div>
    </div>

    <g-link 
      v-for="item in $page.posts.edges"
      :key="item.node.id"
      :to="item.node.path"
      class="journal-post"
    >
      <div class="container journal">
        <h2 class="journal-title">{{ item.node.title }}</h2>
        <p class="journal-excerpt">{{ item.node.content }}</p>
      </div>
    </g-link>
      
  </Layout>
</template>

<page-query>
query {
  posts: allStrapiPosts {
    edges {
      node {
        id
        title
        content
        path
      }
    }
  }
}
</page-query>

<script>
export default {
  created() {
    const data = 1
    console.log(`object${data}`)
  }
}
</script>

<style scoped>
.container.journal {
  max-width: 720px;
}
.journal-hero {
  padding: 4rem 0;
  text-align: center;
  color: var(--color-base-1);
}
.journal-header {
  font-size: 3rem;
  font-weight: 700;
  padding: 0;
  margin: 0;
}
.journal-post {
  display: block;
  padding: 2rem 0;
  text-decoration: none;
  transition: background 0.5s ease;
}
.journal-post > * {
  transition: transform 0.5s ease;
}
.journal-post:hover {
  background-color: var(--color-base-1);
}
.journal-post:hover > * {
  transform: translateX(4rem);
}
.journal-post h1,
.journal-post h2 {
  margin: 0;
  padding: 0;
}
.journal-title {
  font-size: 2rem;
  color: var(--color-contrast);
}
.journal-excerpt {
  color: var(--color-contrast-1);
}

@media (min-width: 560px) {
  .journal-post {
    padding: 3rem 0;
  }
}

@media (min-width: 860px) {
  .journal-post {
    padding: 5rem 0;
  }
}
</style>
