<template>
  <q-layout view="hHh Lpr fFf">

    <q-header class="header" :reveal-offset="500" flat>
      <q-toolbar>

        <!-- HERE: Check for buttons padding (not looking good on mobile)-->
        <q-btn padding="10px" flat icon="eva-menu-outline" aria-label="Menu" @click="toggleLeftDrawer" />
        <q-toolbar-title> Menu </q-toolbar-title>

        <q-btn padding="10px" flat icon="eva-plus-outline" @click="toggleLeftDrawer" />
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above :width="200" :breakpoint="500" bordered class="drawer-bg">

      <q-scroll-area class="fit">
        <q-list padding class="menu-list">
          <EssentialLink v-for="link in essentialLinks" :key="link.label" v-bind="link" />
        </q-list>
      </q-scroll-area>




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
    icon: '',
    caption: 'Storage',
    link: 'https://quasar.dev'
  },
  {
    icon: '',
    caption: 'Another Util',
    link: 'https://github.com/quasarframework'
  },
  {
    icon: '',
    caption: 'Settings',
    link: 'https://github.com/quasarframework'
  },
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
  padding: 10px;
}

.drawer-bg {
  background-color: #cbe4f7;
}

.menu-list {
  border-radius: 0 32px 32px 0;
}
</style>