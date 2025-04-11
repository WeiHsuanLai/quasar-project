<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          天地良心的網頁
        </q-toolbar-title>

        <div>哈喽</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      bordered
    >
      <q-list class="sidebar-nav">
        <q-item-label
          header
        >
          導覽列
        </q-item-label>

        <EssentialLink
          v-for="link in linksList"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup>
import { ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: '首頁',
    caption: '回首頁',
    icon: 'home',
    to: '/home',
  },
  {
    title: '關於我們',
    caption: 'About Page',
    icon: 'info',
    to: '/about',
  },
  {
    title: '我的Github',
    caption: 'MyGithub',
    icon: 'fa-brands fa-github',
    link: 'https://github.com/WeiHsuanLai',
  },
]

const leftDrawerOpen = ref(false)

function toggleLeftDrawer () {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
