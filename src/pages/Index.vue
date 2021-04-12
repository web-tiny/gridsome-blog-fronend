<template>
  <Layout>

    <div class="container">
      <Hero />
      <ProjectsGrid :projects="$page.projects.edges" />
    </div>
    <LatestJournals :journals="$page.projects.edges" />

  </Layout>
</template>

<page-query>
query{
  projects: allStrapiPosts {
    edges {
      node {
        id
        title
        content
        path
        bref
        image {
          id
          url
        }
      }
    }
  }
}
</page-query>

<script>
import Hero from "@/components/Hero"
import LatestJournals from "@/components/LatestJournals"
import ProjectsGrid from "@/components/ProjectsGrid"

export default {
  metaInfo: {
    title: 'home!'
  },
  components: {
    Hero,
    LatestJournals,
    ProjectsGrid
  }
}
</script>
