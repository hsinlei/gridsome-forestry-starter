<template>
  <Layout>
    <div class="event">
      <div class="container event-container">

        <div class="event-header">
          <h1 v-html="$page.post.title" class="event-title" />
          <div class="event-meta">
            <div class="event-author">
              <span class="label">Author</span>
              <span class="author-name" v-text="$page.post.author" />
            </div>
            <div class="event-date">
              <span class="label">Date</span>
              <div v-text="$page.post.date"/>
            </div>
            <div class="event-time">
              <span class="label">Time</span>
              <span>{{ $page.post.timeToRead }} min read</span>
            </div>
          </div>          
        </div>

        <eventContent :content="$page.post.content" />

      </div>
    </div>
  </Layout>
</template>

<page-query>
query eventPost ($path: String!) {
  post: eventPost (path: $path) {
    title
    author
    date (format: "D. MMMM YYYY")
    timeToRead
    content
  }
}
</page-query>

<script>
import eventContent from "@/components/eventContent"

export default {
  components: {
    eventContent
  },
  metaInfo () {
    return {
      title: this.$page.post.title
    }
  }
}
</script>

<style scoped>
.event-container {
  max-width: 840px;
}
.event-header {
  padding: 2rem 0 4rem 0;
}
.event-title {
  font-size: 4rem;
  margin: 0 0 4rem 0;
  padding: 0;
}
.event-meta {
  display: flex;
  flex-wrap: wrap;
  font-size: 0.8rem;
}
.event-meta > div {
  margin-right: 4rem;
}
.event-meta > div:last-of-type {
  margin: 0;
}
</style>
