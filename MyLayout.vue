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
        icon="folder">
          <q-list link>
            <q-item>
              <q-item-side icon="create_new_folder" inverted color="primary" />
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
              <q-item-side icon="more_horiz" inverted color="primary" />
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
        icon="visibility">
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
        icon="edit">
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
        icon="crop_landscape">
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
        icon="build">
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
                <q-item-tile label >How to use this App</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" size="24px" color="amber" title="Click for more information">
              </q-icon>
              <q-popover>
                <q-card inline style="width: 500px">
                  <q-card-title>How to use this App</q-card-title>
                  <q-card-main>
                    <p>
                      <br><br>
                      This app is a tool for you to process your images. Just go to the left-hand q-item-side
                      of the window to find blocks from different categories. By clicking <strong>Add</strong>,
                      you can generate a block.
                      <br><br>
                      Each block has its own functions and parameters which you can read more about by clicking the
                      <strong>icon</strong> next to the <strong>Add</strong> button. You can also find more information
                      on each block's function by following the links.
                      <br><br>
                      You can connect blocks to each other by moving a block to the <strong>lower edge</strong> of another block.
                      Compatible blocks will snap, while incompatible ones will not. You can see which blocks are compatible by
                      clicking the icon next to the Add button again. Your currently moving block's <strong>Input</strong>
                      has to be of the same type as the <strong>Output</strong> of the block you're trying to attach to.
                      <br><br>
                      To create a process, just attach any block with <strong>Input: Image</strong> to the <strong>Starting Block</strong>.
                      After you're finished building a chain of blocks, just hit the <strong>Run Program</strong> button to
                      see it live in action.
                      <br><br>
                      For more information, click on the <strong>Information Icons</strong> throughout or contact us through
                      media given in the <strong>About this App</strong> section.
                    </p>
                  </q-card-main>
                </q-card>
              </q-popover>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="sentiment_satisfied_alt" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >About this App</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" size="24px" color="amber" title="Click for more information">
              </q-icon>
              <q-popover>
                <q-card inline style="width: 500px">
                  <q-card-title>About this App</q-card-title>
                  <q-card-main>
                    <p style="color: grey;">V 0.2 Last modified: Feb 12, 2019 11:59 pm EST</p>
                    <p>
                      <br><br>
                      This app has been created for the project <strong>Visual Programming</strong>.
                      <br><br><br>
                      <strong>Contact us via: </strong>
                      <br><br>
                      <span style="color: blue; text-decoration: underline; padding-left: 50px;">tensei-shitara@slime.datta.ken</span>
                      <br><br>
                      or <strong>call:</strong>
                      <br><br>
                      <strong style="padding-left: 50px;">001-000-TENSEI (001-000-123-4567)</strong>
                    </p>
                  </q-card-main>
                </q-card>
              </q-popover>
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
                @click.native="emit('runProgram')"
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
        icon="photo"
      >
    <q-list link>
      <q-item>
        <q-item-side icon="invert_colors" inverted color="blue" />
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
      <q-item>
        <q-item-side icon="rotate_left" inverted color="blue" />
        <q-item-main @click.native="emit('addBlock', 'rotation')">
          <q-item-tile label>Rotation</q-item-tile>
        </q-item-main>
        <q-btn
            color="blue"
            size="sm"
            label="add"
            align="center"
            @click="emit('addBlock', 'rotation')"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
          <q-popover>
            <q-card inline style="width: 500px">
              <q-card-title>Rotation</q-card-title>
              <q-card-main>
                <p>Input: Image ・ Output: Image</p>
                <p>Rotates an image according to an input in degrees. Positive numbers will rotate clockwise.
                </p>
                <a href="https://en.wikipedia.org/wiki/Rotation_(mathematics)" target="_blank">Read more on rotation</a>
              </q-card-main>
            </q-card>
          </q-popover>
        </q-icon>
      </q-item>
      <q-item-separator inset />
      <q-item>
        <q-item-side icon="lens" inverted color="blue" />
        <q-item-main @click.native="emit('addBlock', 'greyscaling')">
          <q-item-tile label>Greyscaling</q-item-tile>
        </q-item-main>
        <q-btn
            color="blue"
            size="sm"
            label="add"
            align="center"
            @click="emit('addBlock', 'greyscaling')"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
          <q-popover>
            <q-card inline style="width: 500px">
              <q-card-title>Greyscaling</q-card-title>
              <q-card-main>
                <p>Input: Image ・ Output: Image</p>
                <p>Applies greyscaling to each pixel of an image. Given a selection of colour channels,
                   the grey value of each pixel will be the mean of all selected colour channels.
                   Pixel values range from <strong>0</strong> (weakest) to <strong>255</strong> (strongest).
                </p>
                <a href="https://en.wikipedia.org/wiki/Grayscale" target="_blank">Read more on greyscale</a>
              </q-card-main>
            </q-card>
          </q-popover>
        </q-icon>
      </q-item>
      <q-item-separator inset />
      <q-item>
        <q-item-side icon="flare" inverted color="blue" />
        <q-item-main @click.native="emit('addBlock', 'noiseRemoval')">
          <q-item-tile label>Noise Removal</q-item-tile>
        </q-item-main>
        <q-btn
            color="blue"
            size="sm"
            label="add"
            align="center"
            @click="emit('addBlock', 'noiseRemoval')"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
          <q-popover>
            <q-card inline style="width: 500px">
              <q-card-title>Noise Removal</q-card-title>
              <q-card-main>
                <p>Input: Image ・ Output: Image</p>
                <p>Removes noise in a blurring fashion by admixture of a pixel's neighbouring colour values.
                   Noise Removal can be seen as the counterpart to Sharpening.
                  <br>
                  <br>
                  <strong>Parameters:</strong>
                  <ul>
                    <br>
                    <li>
                      <strong>Radius (px): </strong>Size of the neighbourhood of admixture
                    </li>
                    <br>
                    <br>
                    <li>
                      <strong>Strength (%): </strong>How much an image pixel will be changed by its neighbours
                    </li>
                    <br>
                    <br>
                    <li>
                      <strong>Threshold (%): </strong>How to identify noise. A value of 100% will consider everything different
                       from the image pixel as noise, whereas a value of 50% will ignore neighbouring image points which are above
                       above and below that threshold, the image pixel itself being centred within its threshold environment.
                    </li>
                  </ul>
                </p>
                <a href="https://en.wikipedia.org/wiki/Noise_reduction" target="_blank">Read more on noise reduction</a>
              </q-card-main>
            </q-card>
          </q-popover>
        </q-icon>
      </q-item>
      <q-item-separator inset />
      <q-item>
        <q-item-side icon="wb_iridescent" inverted color="blue" />
        <q-item-main @click.native="emit('addBlock', 'sharpening')">
          <q-item-tile label>Sharpening</q-item-tile>
        </q-item-main>
        <q-btn
            color="blue"
            size="sm"
            label="add"
            align="center"
            @click="emit('addBlock', 'sharpening')"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
          <q-popover>
            <q-card inline style="width: 500px">
              <q-card-title>Sharpening</q-card-title>
              <q-card-main>
                <p>Input: Image ・ Output: Image</p>
                <p>Sharpens an image by shortening the transition of soft edges to make them harder.
                </p>
                <a href="https://en.wikipedia.org/wiki/Image_editing#Sharpening_and_softening_images" target="_blank">Read more on image sharpening</a>
              </q-card-main>
            </q-card>
          </q-popover>
        </q-icon>
      </q-item>
      <q-item-separator inset />
      <q-item>
        <q-item-side icon="gradient" inverted color="blue" />
        <q-item-main @click.native="emit('addBlock', 'gaussianFilter')">
          <q-item-tile label>Gaussian Filter</q-item-tile>
        </q-item-main>
        <q-btn
            color="blue"
            size="sm"
            label="add"
            align="center"
            @click="emit('addBlock', 'gaussianFilter')"
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
          <q-popover>
            <q-card inline style="width: 500px">
              <q-card-title>Gaussian Filter</q-card-title>
              <q-card-main>
                <p>Input: Image ・ Output: Image</p>
                <p>Applies a bell-shaped Gaussian filter to the image, given the sigma environment.
                   It tends to blur images and remove noise.
                </p>
                <a href="https://en.wikipedia.org/wiki/Gaussian_filter" target="_blank">Read more on Gaussian filters</a>
              </q-card-main>
            </q-card>
          </q-popover>
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
          icon="border_all"
        >
    <q-list link>
      <q-item>
        <q-item-side icon="scatter_plot" inverted color="red" />
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
        icon="vertical_split"
      >
    <q-list link>
      <q-item>
        <q-item-side icon="translate" inverted color="orange" />
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
    icon="poll"
  >
    <q-list link>
      <q-item>
        <q-item-side icon="compare" inverted color="green" />
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
