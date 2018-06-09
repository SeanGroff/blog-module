<template>
<article
  :class="$style.preview"
  class="article--preview">
  <router-link
      :to="{ name: '@nuxtjs/blog:article', params: Object.assign({ id }, $attrs) }"
      class="article--title"
  >
    {{ title }}
  </router-link>
  <div
    :class="$style.meta"
    class="article--meta">
    <time
      :datatime="published_at"
      class="article--time">
      {{ published_at | formatDate }}
    </time>
  </div>
  <p class="article--description">{{ description }}</p>
</article>
</template>

<script>
import { formatDate } from '../mixins/filters'

export default {
  name: 'Article',

  props: {
    id: {
      required: true,
      type: String
    },
    title: {
      required: true,
      type: String
    },
    description: {
      required: true,
      type: String
    },
    published_at: {
      required: true,
      type: String
    },
  },

  filters: { formatDate }
}
</script>

<style module>
.preview {
  margin-bottom: 15px;
}
.meta {
  font-size: .75rem;
  opacity: .75;
}
</style>
