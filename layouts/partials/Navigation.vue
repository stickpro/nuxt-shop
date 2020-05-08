<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <a class="navbar-item" href="https://bulma.io">
        <img src="https://bulma.io/images/bulma-logo.png" width="112" height="28" />
      </a>

      <div class="navbar-burger" @click="showNav = !showNav" :class="{ 'is-active': showNav }">
        <span></span>
        <span></span>
        <span></span>
      </div>
    </div>

    <div class="navbar-menu" :class="{ 'is-active': showNav }">
      <div class="navbar-start">
        <template v-for="category in categories">
          <template v-if="category.children.length">
            <div class="navbar-item is-hoverable has-dropdown" :key="category.slug">
              <nuxt-link :to="{ name: 'categories-slug', params: {slug: category.slug} }" class="navbar-link">{{ category.name }}</nuxt-link>
              <div class="navbar-dropdown">
                <nuxt-link
                  :to="{ name: 'categories-slug', params: {slug: child.slug} }"
                  class="navbar-item"
                  v-for="child in category.children"
                  :key="child.slug"
                >{{ child.name }}</nuxt-link>
              </div>
            </div>
          </template>
          <template v-else>
            <nuxt-link
              :key="category.slug"
              :to="{ name: 'categories-slug', params: {slug: category.slug} }"
              class="navbar-item"
            >{{ category.name }}</nuxt-link>
          </template>
        </template>
      </div>
    </div>
  </nav>
</template>
<script>
import { mapGetters } from "vuex";

export default {
  data: () => ({
    showNav: false
  }),
  computed: {
    ...mapGetters({
      categories: "categories"
    })
  }
};
</script>