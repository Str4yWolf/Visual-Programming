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
        rounded glossy label="File"
        icon="sentiment_satisfied_alt">
          <q-list link>
            <q-item>
              <q-item-side icon="add" inverted color="primary" />
              <q-item-main @click.native="emit('resetAll')">
                <q-item-tile label >Start New Project</q-item-tile>
              </q-item-main> &nbsp;
            <q-icon name="info" size="24px" color="amber" title="Click for more information">
              <q-popover>
                <q-card inline style="width: 500px">
                  <q-card-title>Start New Project</q-card-title>
                  <q-card-main>
                    <p>Start a new project. Please save your current project in order to avoid loss of data.
                    </p>
                  </q-card-main>
                </q-card>
              </q-popover>
            </q-icon>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="..." inverted color="primary" />
              <q-item-main @click.native="emit('resetAll')">
                <q-item-tile label >Load Project</q-item-tile>
              </q-item-main> &nbsp;
            <q-icon name="info" size="24px" color="amber" title="Click for more information">
              <q-popover>
                <q-card inline style="width: 500px">
                  <q-card-title>Load Project</q-card-title>
                  <q-card-main>
                    <p>Load an existing project. Please save your current project in order to avoid loss of data.
                    </p>
                  </q-card-main>
                </q-card>
              </q-popover>
            </q-icon>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="save" inverted color="primary" />
              <q-item-main @click.native="emit('notify', 'Saved project', 'positive')">
                <q-item-tile label >Save Project</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" size="24px" color="amber" title="Click for more information">
                <q-popover>
                <q-card inline style="width: 500px">
                  <q-card-title>Save Project</q-card-title>
                  <q-card-main>
                    <p>Save your project. If this is your first time saving this project, a new file will be created.
                    </p>
                  </q-card-main>
                </q-card>
              </q-popover>
              </q-icon>
            </q-item>
            <q-item-separator inset />
             <!-- <q-item>
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
            <q-item-separator inset /> -->
          </q-list>
        </q-btn-dropdown>
          <q-btn-dropdown
        color="primary"
        rounded glossy label="View"
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
        rounded glossy label="Edit"
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
        rounded glossy label="Window"
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
        rounded glossy label="Tools"
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
        rounded glossy label="Help"
        icon="help">
          <q-list link>
            <q-item>
              <q-item-side icon="help" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >Help</q-item-tile>
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
                <q-item-tile label >About this app</q-item-tile>
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
                color="positive"
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
                icon="play_arrow"
                @click.native="emit('')"
              />&nbsp;
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
  <q-list-header>MAIN MENU</q-list-header>
  <q-btn-dropdown
        split
        color="blue"
        glossy
        size="30px"
        label="Image Processing"
        icon="sentiment_satisfied_alt"
      >
    <q-list link>
      <q-item>
        <q-item-side icon="sentiment_satisfied_alt" inverted color="blue" />
        <q-item-main @click.native="emit('addBlock', 'binarization')">
          <q-item-tile label title="Click to add block">Binarization</q-item-tile>
        </q-item-main>
        <q-btn
            color="blue"
            size="sm"
            label="add"
            align="center"
            @click="emit('addBlock', 'binarization')"
            title="Click to add block"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
          <q-popover>
            <q-card inline style="width: 500px">
              <q-card-title>Binarization</q-card-title>
              <q-card-main>
                <p>Input: Image ・ Output: Image</p>
                <p>Binarizes an image according to a threshold.
                    All pixel values below the threshold will be displayed as black (binary value 0),
                    whereas the remaining pixels will be displayed as white (binary value 1).
                      For coloured pictures, the pixel value is the mean of all channels.
                </p>
                <a href="https://en.wikipedia.org/wiki/Binary_image" target="_blank">Read more on binary images</a>
              </q-card-main>
            </q-card>
          </q-popover>
        </q-icon>
      </q-item>
      <q-item-separator inset />
      <q-item @click.native="notImplemented">
        <q-item-side icon="sentiment_satisfied_alt" inverted color="blue" />
        <q-item-main>
          <q-item-tile label>Rotation</q-item-tile>
        </q-item-main>
        <q-btn
            color="blue"
            outline
            size="sm"
            label="add"
            align="center"
            @click="notImplemented"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
        </q-icon>
      </q-item>
      <q-item-separator inset />
      <q-item @click.native="notImplemented">
        <q-item-side icon="sentiment_satisfied_alt" inverted color="blue" />
        <q-item-main>
          <q-item-tile label>Greyscaling</q-item-tile>
        </q-item-main>
        <q-btn
            color="blue"
            outline
            size="sm"
            label="add"
            align="center"
            @click="notImplemented"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
        </q-icon>
      </q-item>
      <q-item-separator inset />
      <q-item @click.native="notImplemented">
        <q-item-side icon="sentiment_satisfied_alt" inverted color="blue" />
        <q-item-main>
          <q-item-tile label>Noise Removal</q-item-tile>
        </q-item-main>
        <q-btn
            color="blue"
            outline
            size="sm"
            label="add"
            align="center"
            @click="notImplemented"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
        </q-icon>
      </q-item>
      <q-item-separator inset />
      <q-item @click.native="notImplemented">
        <q-item-side icon="sentiment_satisfied_alt" inverted color="blue" />
        <q-item-main>
          <q-item-tile label>Sharpening</q-item-tile>
        </q-item-main>
        <q-btn
            color="blue"
            outline
            size="sm"
            label="add"
            align="center"
            @click="notImplemented"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
        </q-icon>
      </q-item>
      <q-item-separator inset />
      <q-item @click.native="notImplemented">
        <q-item-side icon="sentiment_satisfied_alt" inverted color="blue" />
        <q-item-main>
          <q-item-tile label>Gaussian Filters</q-item-tile>
        </q-item-main>
        <q-btn
            color="blue"
            outline
            size="sm"
            label="add"
            align="center"
            @click="notImplemented"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
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
      <q-item>
        <q-item-side icon="sentiment_satisfied_alt" inverted color="red" />
        <q-item-main @click.native="emit('addBlock', 'clustering')">
          <q-item-tile label title="Click to add block">Clustering</q-item-tile>
        </q-item-main>
        <q-btn
            color="red"
            size="sm"
            label="add"
            align="center"
            @click="emit('addBlock', 'clustering')"
            title="Click to add block"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
          <q-popover>
            <q-card inline style="width: 500px">
              <q-card-title>Clustering</q-card-title>
              <q-card-main>
                <p>Input: Image ・ Output: Image</p>
                <p>Clusters an image into clusters, using a certain method.
                  <ul>
                    <li>
                      <strong>KNN</strong> (K-nearest neighbours): Takes an image data point and clusters it together with its closest neighbours.
                      <br>
                      <a href="https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm" target="_blank">Read more</a>
                      <br>
                      <br>
                    </li>
                    <li>
                      <strong>DBScan</strong> (Density-based spatial clustering of applications with noise): Clusters together image data points with many similar neighbours.
                      <br>
                      <a href="https://en.wikipedia.org/wiki/DBSCAN" target="_blank">Read more</a>
                      <br>
                      <br>
                    </li>
                    <li>
                      <strong>K-Means</strong>: Starts with random cluster centres and repeatedly assigns data points to their closest clusters until (nearly) converged.
                      <br>
                      <a href="https://en.wikipedia.org/wiki/K-means_clustering" target="_blank">Read more</a>
                      <br>
                      <br>
                    </li>
                    <li>
                      <strong>Spectral Clustering</strong>: Clusters according to the eigenvalues of the similarity matrix of the image data.
                      <br>
                      <a href="https://en.wikipedia.org/wiki/Spectral_clustering" target="_blank">Read more</a>
                      <br>
                      <br>
                    </li>
                  </ul>
                </p>
                <a href="https://en.wikipedia.org/wiki/Cluster_analysis" target="_blank">Read more on cluster analysis</a>
              </q-card-main>
            </q-card>
          </q-popover>
        </q-icon>
      </q-item>
      <q-item-separator inset />
      <q-item @click.native="notImplemented">
        <q-item-side icon="sentiment_satisfied_alt" inverted color="red" />
        <q-item-main>
          <q-item-tile label>placeholder 2</q-item-tile>
        </q-item-main>
        <q-btn
            color="red"
            outline
            size="sm"
            label="add"
            align="center"
            @click="notImplemented"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
        </q-icon>
      </q-item>
      <q-item-separator inset />
      <q-item @click.native="notImplemented">
        <q-item-side icon="sentiment_satisfied_alt" inverted color="red" />
        <q-item-main>
          <q-item-tile label>placeholder 3</q-item-tile>
        </q-item-main>
        <q-btn
            color="red"
            outline
            size="sm"
            label="add"
            align="center"
            @click="notImplemented"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
        </q-icon>
      </q-item>
      <q-item-separator inset />
      <q-item @click.native="notImplemented">
        <q-item-side icon="sentiment_satisfied_alt" inverted color="red" />
        <q-item-main>
          <q-item-tile label>placeholder 4</q-item-tile>
        </q-item-main>
        <q-btn
            color="red"
            outline
            size="sm"
            label="add"
            align="center"
            @click="notImplemented"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
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
      <q-item>
        <q-item-side icon="sentiment_satisfied_alt" inverted color="orange" />
        <q-item-main @click.native="emit('addBlock', 'lettersClassification')">
          <q-item-tile label title="Click to add block">Letters Classification</q-item-tile>
        </q-item-main>
        <q-btn
            color="orange"
            size="sm"
            label="add"
            align="center"
            @click="emit('addBlock', 'lettersClassification')"
            title="Click to add block"
          /> &nbsp;
          <q-icon name="info" size="24px" color="amber" title="Click for more information">
          <q-popover>
            <q-card inline style="width: 500px">
              <q-card-title>Letters Classification</q-card-title>
              <q-card-main>
                <p>Input: Image ・ Output: Text</p>
                <p>Tries to classify letters according to a given alphabet using OCR (Optical Character Recognition).
                   These classifications will be output as text. Non-Latin classifications will be romanized, i.e., will be approximated with Latin letters.
                  <br>
                  Enter one of the available alphabets into the text field.
                  <br>
                  <br>
                  <strong>Currently available:</strong>
                  <ul>
                    <li>
                      <strong>Japanese:</strong> Classifies according to the three Japanese scripts of Kanji, Hiragana, and Katakana.
                      <br>
                      <a href="https://en.wikipedia.org/wiki/Japanese_writing_system" target="_blank">Read more on the Japanese writing system</a>
                      <br>
                      <br>
                    </li>
                    <li>
                      <strong>Latin:</strong> Classifies according to the Latin alphabet, including specifics such as accents, umlauts, and some special letters of an otherwise Latin script language.
                      <br>
                      <a href="https://en.wikipedia.org/wiki/Latin_script" target="_blank">Read more on the Latin writing system</a>
                      <br>
                      <br>
                    </li>
                  </ul>
                </p>
                <a href="https://en.wikipedia.org/wiki/Optical_character_recognition" target="_blank">Read more on OCR</a>
              </q-card-main>
            </q-card>
          </q-popover>
        </q-icon>
      </q-item>
      <q-item-separator inset />
      <q-item @click.native="notImplemented">
        <q-item-side icon="sentiment_satisfied_alt" inverted color="orange" />
        <q-item-main>
          <q-item-tile label>placeholder 2</q-item-tile>
        </q-item-main>
        <q-btn
            color="orange"
            outline
            size="sm"
            label="add"
            align="center"
            @click="notImplemented"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
        </q-icon>
      </q-item>
                <q-item-separator inset />
      <q-item @click.native="notImplemented">
        <q-item-side icon="sentiment_satisfied_alt" inverted color="orange" />
        <q-item-main>
          <q-item-tile label>placeholder 3</q-item-tile>
        </q-item-main>
        <q-btn
            color="orange"
            outline
            size="sm"
            label="add"
            align="center"
            @click="notImplemented"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
        </q-icon>
      </q-item>
      <q-item-separator inset />
      <q-item @click.native="notImplemented">
        <q-item-side icon="sentiment_satisfied_alt" inverted color="orange" />
        <q-item-main>
          <q-item-tile label>placeholder 4</q-item-tile>
        </q-item-main>
        <q-btn
            color="orange"
            outline
            size="sm"
            label="add"
            align="center"
            @click="notImplemented"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
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
      <q-item>
        <q-item-side icon="sentiment_satisfied_alt" inverted color="green" />
        <q-item-main @click.native="emit('addBlock', 'cosineSimilarity')">
          <q-item-tile label title="Click to add block">Cosine Similarity</q-item-tile>
        </q-item-main>
        <q-btn
            color="green"
            size="sm"
            label="add"
            align="center"
            @click="emit('addBlock', 'cosineSimilarity')"
            title="Click to add block"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
          <q-popover>
            <q-card inline style="width: 500px">
              <q-card-title>Cosine Similarity</q-card-title>
              <q-card-main>
                <p>Input: Image ・ Output: Output</p>
                <p>Compares two images and outputs their cosine similarity. A value of <strong>1</strong> means <strong>maximum similarity</strong>,
                   whereas a value of <strong>0</strong> means <strong>no similarity</strong>.
                   A value of <strong>-1</strong> means <strong>maximum inverse similarity</strong>.
                  <br>
                  The cosine similarity describes the quotient of the dot product of the two images and the product of their magnitudes.
                   That is,
                   <br><br><span style="padding-left: 125px;"><strong>cos(A, B) = (A・B)/(||A||*||B||)</strong></span>
                </p>
                <a href="https://en.wikipedia.org/wiki/Cosine_similarity" target="_blank">Read more on cosine similarity</a>
              </q-card-main>
            </q-card>
          </q-popover>
        </q-icon>
      </q-item>
      <q-item-separator inset />
      <q-item @click.native="notImplemented">
        <q-item-side icon="sentiment_satisfied_alt" inverted color="green" />
        <q-item-main>
          <q-item-tile label>placeholder 2</q-item-tile>
        </q-item-main>
        <q-btn
            color="green"
            outline
            size="sm"
            label="add"
            align="center"
            @click="notImplemented"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
        </q-icon>
      </q-item>
                <q-item-separator inset />
      <q-item @click.native="notImplemented">
        <q-item-side icon="sentiment_satisfied_alt" inverted color="green" />
        <q-item-main>
          <q-item-tile label>placeholder 3</q-item-tile>
        </q-item-main>
        <q-btn
            color="green"
            outline
            size="sm"
            label="add"
            align="center"
            @click="notImplemented"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
        </q-icon>
      </q-item>
      <q-item-separator inset />
      <q-item @click.native="notImplemented">
        <q-item-side icon="sentiment_satisfied_alt" inverted color="green" />
        <q-item-main>
          <q-item-tile label>placeholder 4</q-item-tile>
        </q-item-main>
        <q-btn
            color="green"
            outline
            size="sm"
            label="add"
            align="center"
            @click="notImplemented"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
        </q-icon>
      </q-item>
    </q-list>
  </q-btn-dropdown> &nbsp;
              <q-btn
                color="indigo"
                glossy
                disable
                class="full-width"
                size="lg"
                rounded
                label="Customize block"
                align="center"
                icon="sentiment_satisfied_alt"
              /> &nbsp;
              <q-btn
                color="blue-grey"
                glossy
                disable
                class="full-width"
                size="lg"
                rounded
                label="Customize routine"
                align="center"
                icon="sentiment_satisfied_alt"
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
      this.$root.$emit(msg, ...args)
    }
  }
}
</script>
<style>
</style>
