<template>
  <q-layout view="lHh Lpr lFf"
  :content-class="$q.theme === 'mat' ? 'bg-grey-9' : null"
  >
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
  <q-btn-group>
  <q-btn-dropdown
        color="primary"
        rounded glossy label="tensei"
        icon="sentiment_satisfied_alt">
          <q-list link>
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
          </q-list>
        </q-btn-dropdown>
          <q-btn-dropdown
        color="primary"
        rounded glossy label="shitara"
        icon="sentiment_satisfied_alt">
          <q-list link>
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
          </q-list>
        </q-btn-dropdown>
          <q-btn-dropdown
        color="primary"
        rounded glossy label="slime"
        icon="sentiment_satisfied_alt">
          <q-list link>
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
          </q-list>
        </q-btn-dropdown>
          <q-btn-dropdown
        color="primary"
        rounded glossy label="datta"
        icon="sentiment_satisfied_alt">
          <q-list link>
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
          </q-list>
        </q-btn-dropdown>
          <q-btn-dropdown
        color="primary"
        rounded glossy label="ken"
        icon="sentiment_satisfied_alt">
          <q-list link>
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main>
            <q-item-side right icon="info" color="amber" />
            </q-item>
            <q-item-separator inset />
          </q-list>
        </q-btn-dropdown>
      </q-btn-group>
         <q-toolbar-title>
          <div style="text-align: right;">Quasar App</div>
          <div slot="subtitle" style="text-align: right;">Running on Quasar v{{ $q.version }}</div>
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
        <q-list-header>MAIN MENU &nbsp; &nbsp; &nbsp;
        <!-- Lets the user toggle notifications on several actions -->
        <q-btn
                color="primary"
                size="sm"
                label="Toggle Notifications"
                align="center"
                @click.native="emit('toggleNotifications')"
              />
              <!-- reset to initial state -->
        <q-btn
                color="grey"
                size="sm"
                label="Reset All"
                align="center"
                @click.native="emit('resetAll')"
              />
        </q-list-header>
  <q-btn-dropdown
        split
        color="blue"
        glossy
        size="30px"
        label="Image Processing"
        icon="sentiment_satisfied_alt"
      >
        <q-list link>
          <!-- <q-item v-close-overlay @click.native="showNotification"> -->
          <q-item v-close-overlay>
            <q-item-side icon="sentiment_satisfied_alt" inverted color="blue" />
            <q-item-main>
              <q-item-tile label>Binarization</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="primary"
                size="sm"
                label="add"
                align="right"
                @click="emit('addBlock', 'binarization')"
              />
            <q-item-side right icon="info" color="amber" />
          </q-item>
          <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="blue" />
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
            <q-item-side icon="sentiment_satisfied_alt" inverted color="blue" />
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
            <q-item-side icon="sentiment_satisfied_alt" inverted color="blue" />
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
        icon="sentiment_satisfied_alt"
      >
        <q-list link>
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="red" />
            <q-item-main>
              <q-item-tile label>placeholder 1</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
          <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="red" />
            <q-item-main>
              <q-item-tile label>placeholder 2</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="red" />
            <q-item-main>
              <q-item-tile label>placeholder 3</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="red" />
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
        color="orange"
        glossy
        size="30px"
        label="Optical Character Recognition"
        icon="sentiment_satisfied_alt"
      >
        <q-list link>
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="orange" />
            <q-item-main>
              <q-item-tile label>Letters Classification</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="orange"
                size="sm"
                label="add"
                align="right"
                @click="emit('addBlock', 'lettersClassification')"
              />
            <q-item-side right icon="info" color="amber" />
          </q-item>
          <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="orange" />
            <q-item-main>
              <q-item-tile label>placeholder 2</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="orange" />
            <q-item-main>
              <q-item-tile label>placeholder 3</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="orange" />
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
        icon="sentiment_satisfied_alt"
      >
        <q-list link>
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="green" />
            <q-item-main>
              <q-item-tile label>placeholder 1</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
          <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="green" />
            <q-item-main>
              <q-item-tile label>placeholder 2</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="green" />
            <q-item-main>
              <q-item-tile label>placeholder 3</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="green" />
            <q-item-main>
              <q-item-tile label>placeholder 4</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-item-side right icon="info" color="amber" />
          </q-item>
        </q-list>
</q-btn-dropdown>
        </q-list>
        <q-btn
                color="secondary"
                glossy
                size="xl"
                rounded
                label="Run Program"
                align="center"
                class="full-width"
                icon="sentiment_satisfied_alt"
                @click.native="emit('')"
              />
    </q-layout-drawer>
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
      leftDrawerOpen: this.$q.platform.is.desktop
    }
  },
  methods: {
    openURL,
    notImplemented: function () {
      alert('Not implemented yet (...) We\'ll work on that')
    },
    emit: function (msg, ...args) {
      console.log('called emit from layout with msg ' + msg)
      this.$root.$emit(msg, ...args)
    },
    showNotification: function () {
      console.log('called showNotification in Layout')
    }
  }
}
</script>
<style>
</style>
