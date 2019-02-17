<template>
  <q-layout  view="hHh Lpr lff">
    <q-header>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          aria-label="Menu"
        >
          <q-icon name="menu" />
        </q-btn>

        <q-toolbar-title>
          YetiForceCRM Settings
        </q-toolbar-title>

        <div>Login / Logout</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      bordered
      content-class="bg-grey-2"
    >
      <q-list bordered class="rounded-borders">
      <q-item clickable v-ripple>
        <q-item-section avatar>
          <q-icon name="home" />
        </q-item-section>
        <q-item-section>{{$t('LBL_HOME')}}</q-item-section>
      </q-item>
      <q-expansion-item
          expand-separator
          icon="security"
          :label="$t('LBL_PERMISSIONS')"
          default-closed
          :content-inset-level="1"
        >
        <q-list>
            <q-item clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="group" />
              </q-item-section>
              <q-item-section>{{$t('LBL_USERS')}}</q-item-section>
            </q-item>
        </q-list>
      </q-expansion-item>
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
  name: 'Basic',
  data () {
    return {
      leftDrawerOpen: this.$q.platform.is.desktop,
      simple: [
        {
          label: 'Satisfied customers (with avatar)',
          avatar: 'https://cdn.quasar-framework.org/img/boy-avatar.png',
          children: [
            {
              label: 'Good food (with icon)',
              icon: 'restaurant_menu',
              children: [
                { label: 'Quality ingredients' },
                { label: 'Good recipe' }
              ]
            },
            {
              label: 'Good service (disabled node with icon)',
              icon: 'room_service',
              children: [
                { label: 'Prompt attention' },
                { label: 'Professional waiter' }
              ]
            },
            {
              label: 'Pleasant surroundings (with icon)',
              icon: 'photo',
              children: [
                {
                  label: 'Happy atmosphere (with image)',
                  img: 'https://cdn.quasar-framework.org/img/logo_calendar_128px.png'
                },
                { label: 'Good table presentation' },
                { label: 'Pleasing decor' }
              ]
            }
          ]
        }
      ],
      expanded: ['Satisfied customers (with avatar)', 'Good food (with icon)']
    }
  },
  methods: {
    openURL
  }
}
</script>

<style>
</style>
