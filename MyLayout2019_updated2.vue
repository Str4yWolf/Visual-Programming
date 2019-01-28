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
              </q-item-main> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
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
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
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
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
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
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
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
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >dummy</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
            </q-item>
            <q-item-separator inset />
          </q-list>
        </q-btn-dropdown>
      </q-btn-group> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
             <!-- reset to initial state -->
              <q-btn
                class="on-right"
                color="white"
                text-color="blue"
                size="md"
                label="Reset All"
                align="center"
                @click.native="emit('resetAll')"
              /> &nbsp;
              <!-- Lets the user toggle notifications on several actions -->
              <q-btn
                class="on-right"
                color="primary"
                glossy
                size="md"
                label="Toggle Notifications"
                align="center"
                @click.native="emit('toggleNotifications')"
              /> &nbsp;
              <!-- runs the generated process chain -->
              <q-btn
                class="on-right"
                color="secondary"
                glossy
                size="md"
                rounded
                label="Run Program"
                align="center"
                icon="sentiment_satisfied_alt"
                @click.native="emit('')"
              />
         <!-- <q-toolbar-title> -->
          <!-- <div style="text-align: right;">Quasar App</div> -->
          <!-- <div slot="subtitle" style="text-align: right;">Running on Quasar v{{ $q.version }}</div> -->
        <!-- </q-toolbar-title> -->
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
                color="blue"
                size="sm"
                label="add"
                align="center"
                @click="emit('addBlock', 'binarization')"
              /> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
          </q-item>
          <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="blue" />
            <q-item-main>
              <q-item-tile label>Rotation</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="blue"
                outline
                size="sm"
                label="add"
                align="center"
                @click="notImplemented"
              /> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="blue" />
            <q-item-main>
              <q-item-tile label>Greyscaling</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="blue"
                outline
                size="sm"
                label="add"
                align="center"
                @click="notImplemented"
              /> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="blue" />
            <q-item-main>
              <q-item-tile label>Noise Removal</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="blue"
                outline
                size="sm"
                label="add"
                align="center"
                @click="notImplemented"
              /> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
          </q-item>
          <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="blue" />
            <q-item-main>
              <q-item-tile label>Sharpening</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="blue"
                outline
                size="sm"
                label="add"
                align="center"
                @click="notImplemented"
              /> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
          </q-item>
          <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="blue" />
            <q-item-main>
              <q-item-tile label>Gaussian Filters</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="blue"
                outline
                size="sm"
                label="add"
                align="center"
                @click="notImplemented"
              /> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
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
            <q-btn
                color="red"
                outline
                size="sm"
                label="add"
                align="center"
                @click="notImplemented"
              /> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
          </q-item>
          <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="red" />
            <q-item-main>
              <q-item-tile label>placeholder 2</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="red"
                outline
                size="sm"
                label="add"
                align="center"
                @click="notImplemented"
              /> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="red" />
            <q-item-main>
              <q-item-tile label>placeholder 3</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="red"
                outline
                size="sm"
                label="add"
                align="center"
                @click="notImplemented"
              /> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="red" />
            <q-item-main>
              <q-item-tile label>placeholder 4</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="red"
                outline
                size="sm"
                label="add"
                align="center"
                @click="notImplemented"
              /> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
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
                align="center"
                @click="emit('addBlock', 'lettersClassification')"
              /> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
          </q-item>
          <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="orange" />
            <q-item-main>
              <q-item-tile label>placeholder 2</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="orange"
                outline
                size="sm"
                label="add"
                align="center"
                @click="notImplemented"
              /> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="orange" />
            <q-item-main>
              <q-item-tile label>placeholder 3</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="orange"
                outline
                size="sm"
                label="add"
                align="center"
                @click="notImplemented"
              /> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="orange" />
            <q-item-main>
              <q-item-tile label>placeholder 4</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="orange"
                outline
                size="sm"
                label="add"
                align="center"
                @click="notImplemented"
              /> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
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
            <q-btn
                color="green"
                outline
                size="sm"
                label="add"
                align="center"
                @click="notImplemented"
              /> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
          </q-item>
          <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="green" />
            <q-item-main>
              <q-item-tile label>placeholder 2</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="green"
                outline
                size="sm"
                label="add"
                align="center"
                @click="notImplemented"
              /> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="green" />
            <q-item-main>
              <q-item-tile label>placeholder 3</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="green"
                outline
                size="sm"
                label="add"
                align="center"
                @click="notImplemented"
              /> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
          </q-item>
                    <q-item-separator inset />
          <q-item v-close-overlay @click.native="showNotification">
            <q-item-side icon="sentiment_satisfied_alt" inverted color="green" />
            <q-item-main>
              <q-item-tile label>placeholder 4</q-item-tile>
              <q-item-tile sublabel></q-item-tile>
            </q-item-main>
            <q-btn
                color="green"
                outline
                size="sm"
                label="add"
                align="center"
                @click="notImplemented"
              /> &nbsp;
            <q-icon name="info" color="amber">
            <q-tooltip anchor="center right" self="center left" :offset="[10, 10]">
            some tooltip
            </q-tooltip>
            </q-icon>
          </q-item>
        </q-list>
</q-btn-dropdown>
              <q-btn
                color="indigo"
                glossy
                class="full-width"
                size="xl"
                rounded
                label="Customize block"
                align="center"
                icon="sentiment_satisfied_alt"
                @click.native="emit('')"
              />
              <q-btn
                color="blue-grey"
                glossy
                class="full-width"
                size="xl"
                rounded
                label="Customize routine"
                align="center"
                icon="sentiment_satisfied_alt"
                @click.native="emit('')"
              />
        </q-list>
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
      alert('Not implemented yet (...) We\'ll work on that (or maybe not =)')
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
