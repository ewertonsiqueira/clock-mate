<template>
  <v-footer
    app
    height="40"
  >
    <a
      v-for="item in personalLinks"
      :key="item.title"
      class="d-inline-block mx-2 social-link"
      :href="item.href"
      rel="noopener noreferrer"
      target="_blank"
      :title="item.title"
    >
      <v-icon
        :icon="item.icon"
        :size="20"
      />
    </a>

    <div
      class="text-caption text-disabled"
      style="position: absolute; right: 16px;"
    >
      &copy; 2025-{{ (new Date()).getFullYear() }} <span class="d-none d-sm-inline-block">Vuetify, LLC</span>
      —
      <a
        class="text-decoration-none on-surface"
        href="https://vuetifyjs.com/about/licensing/"
        rel="noopener noreferrer"
        target="_blank"
      >
        MIT License
      </a>
    </div>
  </v-footer>
</template>

<script setup>
  const personalLinks = [
    {
      title: 'Meu LinkedIn',
      icon: 'mdi-linkedin',
      href: 'https://www.linkedin.com/in/ewerton-siqueira-173b981aa/',
    },
    {
      title: 'Meu GitHub',
      icon: 'mdi-github',
      href: 'https://github.com/ewertonsiqueira',
    },
  ]
</script>

<style scoped lang="sass">

</style>
