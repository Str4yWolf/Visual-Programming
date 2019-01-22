<template>
  <q-layout view="lHh Lpr lFf">
    <q-layout-header>
      <q-toolbar
        color="primary"
        :glossy="$q.theme === 'mat'"
        :inverted="$q.theme === 'ios'"
      >
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
          Quasar App
          <div slot="subtitle">Running on Quasar v{{ $q.version }}</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-layout-header>
     <q-layout-drawer
      v-model="leftDrawerOpen"
      :content-class="$q.theme === 'mat' ? 'bg-grey-2' : null"
    >
      <q-list
        no-border
        link
        inset-delimiter
      >
        <q-list-header>Main Menu
        </q-list-header>
     <!--   <q-item @click.native="openURL('http://quasar-framework.org')">
          <q-item-side icon="school" />
          <q-item-main label="Docs" sublabel="quasar-framework.org" />
        </q-item>
        <q-item @click.native="openURL('https://github.com/quasarframework/')">
          <q-item-side icon="code" />
          <q-item-main label="GitHub" sublabel="github.com/quasarframework" />
        </q-item>
        <q-item @click.native="openURL('https://discord.gg/5TDhbDg')">
          <q-item-side icon="chat" />
          <q-item-main label="Discord Chat Channel" sublabel="https://discord.gg/5TDhbDg" />
        </q-item>
        <q-item @click.native="openURL('http://forum.quasar-framework.org')">
          <q-item-side icon="record_voice_over" />
          <q-item-main label="Forum" sublabel="forum.quasar-framework.org" />
        </q-item>
        <q-item @click.native="openURL('https://twitter.com/quasarframework')">
          <q-item-side icon="rss feed" />
          <q-item-main label="Twitter" sublabel="@quasarframework" />
        </q-item>
          <q-collapsible group="somegroup" icon="explore" label="First">
    <div>
      Content
    </div>
  </q-collapsible>
  <q-collapsible group="somegroup" icon="perm_identity" label="Second">
    <div>
      Content
    </div>
  </q-collapsible>
  <q-collapsible group="somegroup" icon="shopping_cart" label="Third">
    <div>
      Content
    </div>
  </q-collapsible> -->
  <q-btn-dropdown
        split
        color="blue"
        glossy
        size="30px"
        label="Image Processing"
        icon="folder"
      >
        <q-list link>
          <q-item v-close-overlay @click.native="addBinarization">
            <q-item-side icon="folder" inverted color="blue" />
            <q-item-main>
              <q-item-tile label>Binarization</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="primary"
                size="sm"
                label="add"
                align="right"
                @click="addBinarization"
              />
            <q-item-side right icon="info" color="amber" />
          </q-item>
          <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="folder" inverted color="blue" />
            <q-item-main>
              <q-item-tile label>Rotation</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="primary"
                size="sm"
                label="add"
                align="right"
                @click="notImplemented"
              />
            <q-item-side right icon="info" color="amber" />
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="folder" inverted color="blue" />
            <q-item-main>
              <q-item-tile label>Greyscaling</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="primary"
                size="sm"
                label="add"
                align="right"
                @click="notImplemented"
              />
            <q-item-side right icon="info" color="amber" />
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="folder" inverted color="blue" />
            <q-item-main>
              <q-item-tile label>Noise Removal</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="primary"
                size="sm"
                label="add"
                align="right"
                @click="notImplemented"
              />
            <q-item-side right icon="info" color="amber" />
          </q-item>
        </q-list>
</q-btn-dropdown>
<q-btn-dropdown
        split
        color="red"
        glossy
        size="30px"
        label="Page Layout Analysis / Image Segmentation"
        icon="folder"
      >
        <q-list link>
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="folder" inverted color="red" />
            <q-item-main>
              <q-item-tile label>tensei</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
          <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="folder" inverted color="red" />
            <q-item-main>
              <q-item-tile label>shitara</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="folder" inverted color="red" />
            <q-item-main>
              <q-item-tile label>slime</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="folder" inverted color="red" />
            <q-item-main>
              <q-item-tile label>datta ken</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
        </q-list>
</q-btn-dropdown>
<q-btn-dropdown
        split
        color="orange"
        glossy
        size="30px"
        label="Optical Character Recognition"
        icon="folder"
      >
        <q-list link>
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="folder" inverted color="orange" />
            <q-item-main>
              <q-item-tile label>placeholder 1</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
          <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="folder" inverted color="orange" />
            <q-item-main>
              <q-item-tile label>placeholder 2</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="folder" inverted color="orange" />
            <q-item-main>
              <q-item-tile label>placeholder 3</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="folder" inverted color="orange" />
            <q-item-main>
              <q-item-tile label>placeholder 4</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
        </q-list>
</q-btn-dropdown>
       <q-btn-dropdown
        split
        color="green"
        glossy
        size="30px"
        label="feature extraction / comparison"
        icon="folder"
      >
        <q-list link>
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="folder" inverted color="green" />
            <q-item-main>
              <q-item-tile label>placeholder 1</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
          <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="folder" inverted color="green" />
            <q-item-main>
              <q-item-tile label>placeholder 2</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="folder" inverted color="green" />
            <q-item-main>
              <q-item-tile label>placeholder 3</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="folder" inverted color="green" />
            <q-item-main>
              <q-item-tile label>placeholder 4</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
        </q-list>
</q-btn-dropdown>
      </q-list>
    </q-layout-drawer>
     <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>
<script>
import {openURL} from 'quasar'
export default {
  name: 'MyLayout',
  data () {
    return {
      leftDrawerOpen: this.$q.platform.is.desktop
    }
  },
  methods: {
    openURL,
    addBinarization: function () {
      this.$root.$emit('addblock', 'binarization')
      console.log('addBinarization called from layout')
    },
    notImplemented: function () {
      alert('Not implemented yet (...) We\'ll work on that')
    }
  }
}
</script>
<style>
</style>
