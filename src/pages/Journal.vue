<template>
  <Layout>

    <div class="container">
      <div class="event-hero">
        <h1 class="event-header">
          a wise person once said...
        </h1>
      </div>
    </div>

    <g-link 
      :to="item.node.path"
      v-for="item in $page.posts.edges" 
      :key="item.node.id"
      class="event-post"
    >
      <div class="container event">
        <h2 class="event-title">{{ item.node.title }}</h2>
        <p class="event-excerpt">{{ item.node.excerpt }}</p>
      </div>
    </g-link>
      
  </Layout>
</template>

<page-query>
query event {
	posts: alleventPost {
    edges {
      node {
        id
        path
        title
        excerpt
      }
    }
  }
}
</page-query>

<script>
export default {
}
</script>

<style scoped>
.container.event {
  max-width: 720px;
}
.event-hero {
  padding: 4rem 0;
  text-align: center;
  color: var(--color-base-1);
}
.event-header {
  font-size: 3rem;
  font-weight: 700;
  padding: 0;
  margin: 0;
}
.event-post {
  display: block;
  padding: 2rem 0;
  text-decoration: none;
  transition: background 0.5s ease;
}
.event-post > * {
  transition: transform 0.5s ease;
}
.event-post:hover {
  background-color: var(--color-base-1);
}
.event-post:hover > * {
  transform: translateX(4rem);
}
.event-post h1,
.event-post h2 {
  margin: 0;
  padding: 0;
}
.event-title {
  font-size: 2rem;
  color: var(--color-contrast);
}
.event-excerpt {
  color: var(--color-contrast-1);
}

@media (min-width: 560px) {
  .event-post {
    padding: 3rem 0;
  }
}

@media (min-width: 860px) {
  .event-post {
    padding: 5rem 0;
  }
}
</style>
