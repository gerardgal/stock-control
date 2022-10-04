<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="header" elevated>
      <q-toolbar>
        <q-btn padding="10px" icon="eva-menu" push dense round aria-label="Menu" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          Menu
        </q-toolbar-title>

      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <!-- TODO: Display local time at top -->

        <!-- <q-item-label header>
          Essential Links
        </q-item-label> -->

        <EssentialLink v-for="link in essentialLinks" :key="link.title" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Example link 1',
    caption: 'This is a link',
    icon: '',
    link: 'https://quasar.dev'
  },
  {
    title: 'Example link 2',
    caption: 'This is another link',
    icon: '',
    link: 'https://github.com/quasarframework'
  }
]

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup() {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>

<style>
.header {
  height: 65px;
  padding: 5px;
}
</style>