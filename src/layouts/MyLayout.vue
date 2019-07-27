<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="bg-deep-purple" elevated>
      <q-toolbar>
        <q-btn @click="leftDrawerOpen = !leftDrawerOpen" aria-label="Menu" dense flat>
          <q-icon name="menu" />
        </q-btn>

        <q-toolbar-title>Kanban</q-toolbar-title>

        <div>Login | Register</div>
      </q-toolbar>
    </q-header>

    <q-drawer bordered content-class="bg-grey-2" v-model="leftDrawerOpen">
      <q-list>
        <q-item-label header>Boards</q-item-label>
        <q-item clickable href="https://quasar.dev" tag="a" target="_blank">
          <q-item-section avatar>
            <q-icon name="school" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Workout</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable href="https://github.quasar.dev" tag="a" target="_blank">
          <q-item-section avatar>
            <q-icon name="code" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Kanban</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { openURL } from 'quasar'

export default {
  name: 'MyLayout',
  data () {
    return {
      leftDrawerOpen: false
    }
  },
  methods: {
    openURL
  }
}
</script>

<style>
</style>
