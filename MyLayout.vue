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
              <q-item-main @click.native="checkFileExists(' saving project.')">
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
            <q-item>
              <q-item-side icon="keyboard_tab" inverted color="primary" />
              <q-item-main @click.native="checkFileExists(' exporting results.')">
                <q-item-tile label >Export Results</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" size="24px" color="amber" title="Click for more information">
                <q-popover>
                  <q-card inline style="width: 500px">
                    <q-card-title>Export Results</q-card-title>
                    <q-card-main>
                      <p>Save your file. The file that you're saving is what you can see in the image preview.
                         The file type will correspond to what you get as the output type of your last block connected to the starting block.
                      </p>
                    </q-card-main>
                  </q-card>
                </q-popover>
              </q-icon>
            </q-item>
          </q-list>
        </q-btn-dropdown>
          <q-btn-dropdown
        color="primary"
        rounded glossy label="View"
        icon="visibility">
          <q-list link>
            <q-item>
              <q-item-side icon="book" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >Documentation</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" size="24px" color="amber" title="Click for more information">
              </q-icon>
              <q-popover>
                <q-card inline style="width: 1000px">
                  <q-card-title>Documentation</q-card-title>
                  <q-card-main>
                    <p style="color: grey;">Tensei XP VPL</p>
                    <p>
                      <br><br>
                      Our VPL app is dedicated to those of you who would like to perform advanced <strong>Digital Image Analysis (DIA)</strong>
                       on images of text but don't want to spend too much time on learning a programming language.
                       For our intuitive block-based VPL paradigm will let you safely try which building blocks
                       fit and which don't.
                      <br>
                       At our VPL's core lies the <strong>main "construction" area</strong> where you can create your own functions
                       with small elemental blocks you can choose from the left. Given an input text on an image, you can then decide which functions you would like to perform
                       in what order and with which parameters. An <strong>image preview</strong> will give immediate feedback on what your output image will look like.
                       Try out different configurations and settings and choose the option that best fit you. And when you are content with the results,
                       you can think about what format your output file(s) will be (e.g., image or text).
                      <br><br><br><br>
                      <strong><h5>1 - Basics</h5></strong>
                      The following are some basics for you to get started right away.
                      <br><br>
                      <strong>Adding a Block</strong>
                      <br>
                      By selecting a category on the left and clicking the <strong>Add</strong> button or the name label, you can generate a block
                      <br><br>
                      <strong>Block Info</strong>
                      <br>
                      Each block has its own functions and parameters which you can read more about by clicking the
                       <strong>icon</strong> next to the <strong>Add</strong> button. You can also find more information
                       on each block's function by following the links.
                      <br><br>
                      <strong>Connecting Blocks</strong>
                      <br>
                      You can connect blocks to each other by moving a block to the <strong>lower edge</strong> of another block.
                       Compatible blocks will snap, while incompatible ones will not. You can see which blocks are compatible by
                       viewing the block info next to the Add button. Your currently moving block's <strong>Input</strong>
                       has to be of the same type as the <strong>Output</strong> of the block you're trying to attach to.
                      <br><br>
                      <strong>Chaining Blocks and Running a Process</strong>
                      <br>
                      To create a process, just attach any block with <strong>Input: Image</strong> to the <strong>Starting Block</strong>.
                       After you're finished building a chain of blocks, just hit the <strong>Run Program</strong> button on the top right to
                       see it live in action.
                      <br><br>
                      <strong>Encapsulation</strong>
                      <br>
                      Because there might be long chains of blocks involved in your image steps, you can encapsulate a moving chain of blocks by moving it against the <strong>Encapsulator</strong>.
                       If you can't see the <strong>Encapsulator</strong>, then press <strong>Toggle Encapsulator</strong> on the bottom left. You can name your resulting <strong>Encapsulation</strong>
                       and decapsulate it again by moving it against the <strong>Encapsulator again</strong>.
                      <br><br>
                      <strong>Save and Load Project, Export</strong>
                      <br>
                      By default, you will have started a new project by running this program. On the top left of the menu under <strong>File</strong>, you can choose to
                       save, load, or even start a new project by clicking their respective labels. When you are done, you can export your processed file.
                      <br><br>
                      <strong>Notifications</strong>
                      <br>
                      By default, you will see notifications on actions at the bottom. You can toggle these by clicking the <strong>Toggle Notifications</strong> button on the top right.
                      <br><br>
                      <strong>Reset Blocks</strong>
                      <br>
                      You can reset all blocks to the initial state by clicking <strong>Reset Blocks</strong> next to the <strong>Toggle Notifications</strong> button.
                       Make sure that you've saved your project in order to avoid any loss of data.
                      <br><br><br><br>
                      <strong><h5>2 - Blocks</h5></strong>
                      You'll find some information on blocks here.
                      <br><br>
                      <strong>Binarization</strong>
                      <br>
                      <p>Input: Image ・ Output: Image</p>
                      <p>Binarizes an image according to a threshold.
                          All pixel values below the threshold will be displayed as black (binary value 0),
                          whereas the remaining pixels will be displayed as white (binary value 1).
                            For coloured pictures, the pixel value is the mean of all channels.
                      </p>
                      <a href="https://en.wikipedia.org/wiki/Binary_image" target="_blank">Read more on binary images</a>
                      <br><br>
                      <strong>Rotation</strong>
                      <br>
                      <p>Input: Image ・ Output: Image</p>
                      <p>Rotates an image according to an input in degrees. Positive numbers will rotate clockwise.
                      </p>
                      <a href="https://en.wikipedia.org/wiki/Rotation_(mathematics)" target="_blank">Read more on rotation</a>
                      <br><br>
                      <strong>Greyscaling</strong>
                      <br>
                      <p>Input: Image ・ Output: Image</p>
                      <p>Applies greyscaling to each pixel of an image. Given a selection of colour channels,
                          the grey value of each pixel will be the mean of all selected colour channels.
                          Pixel values range from <strong>0</strong> (weakest) to <strong>255</strong> (strongest).
                      </p>
                      <a href="https://en.wikipedia.org/wiki/Grayscale" target="_blank">Read more on greyscale</a>
                      <br><br>
                      <strong>Noise Removal</strong>
                      <br>
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
                      <br><br>
                      <strong>Sharpening</strong>
                      <br>
                      <p>Input: Image ・ Output: Image</p>
                      <p>Sharpens an image by shortening the transition of soft edges to make them harder.
                      </p>
                      <a href="https://en.wikipedia.org/wiki/Image_editing#Sharpening_and_softening_images" target="_blank">Read more on image sharpening</a>
                      <br><br>
                      <strong>Gaussian Filter</strong>
                      <br>
                      <p>Input: Image ・ Output: Image</p>
                      <p>Applies a bell-shaped Gaussian filter to the image, given the sigma environment.
                        It tends to blur images and remove noise.
                      </p>
                      <a href="https://en.wikipedia.org/wiki/Gaussian_filter" target="_blank">Read more on Gaussian filters</a>
                      <br><br>
                      <strong>Clustering</strong>
                      <br>
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
                          </li>
                        </ul>
                      </p>
                      <br><br>
                      <strong>Letters Classification</strong>
                      <br>
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
                      <br><br>
                      <strong>Cosine Similarity</strong>
                      <br>
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
                      <br><br>
                      <strong>Encapsulator</strong>
                      <br>
                      <p>
                        Move a chain of blocks against the Encapsulator and it will generate a single block "<strong>Encapsulation</strong>" from it.
                        Move an Encapsulation block against the Encapsulator and you will get the blocks it contains.
                      </p>
                      <br><br>
                      <strong>Encapsulation</strong>
                      <br>
                      <p>
                        An encapsulation of the blocks you moved against the <strong>Encapsulator</strong>.
                        Enter a name in the text field to distinguish your encapsulations.
                        A <strong>Loop</strong> on this block will apply to all of the blocks it contains.
                        <br>
                        When you delete this block, all of the contained blocks will also disappear. If you have also
                        deleted the <strong>Starting Block</strong>, then hit <strong>Reset Blocks</strong> to get it back.
                      </p>
                      <br><br>
                      <strong>Loop (Beta)</strong>
                      <br>
                      <p>
                        Perform a chain of blocks as much as you enter into the input field. You can attach this block to the left of any type of normal block.
                         Currently, it works only on one block at a time
                         and the <strong>+/-</strong> buttons don't work yet. A workaround could be to <strong>encapsulate</strong> your chain of blocks and
                         attach this for loop to the encapsulation instead.
                      </p>
                      <br><br>
                      <strong>Select Region (Beta)</strong>
                      <br>
                      <p>
                        Select a region of interest on which actions will be performed.
                         Currently, you can only select the entire image region. Thus, this component
                         acts as an <strong>Image Preview</strong> of the input image at the moment.
                        <br>
                        Press <strong>Select</strong> to confirm, or <strong>Cancel</strong> to revert to original image.
                      </p>
                      <br><br>
                      <strong>Image Preview</strong>
                      <br>
                      <p>
                        Displays a preview of the image that results from performing your chain
                         of blocks as a program. Hit the <strong>Run Program</strong> button to
                         run your program.
                      </p>
                      <br><br>
                      <strong>More Info</strong>
                      <br><br><br><br>
                      For more information, click on the <strong>Information Icons</strong> throughout or contact us through
                       media given in the <strong>About this App</strong> section.
                  </q-card-main>
                </q-card>
              </q-popover>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="info" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >Terms of Use</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" size="24px" color="amber" title="Click for more information">
              </q-icon>
              <q-popover>
                <q-card inline style="width: 1000px">
                  <q-card-title>Terms of Use</q-card-title>
                  <q-card-main>
                    <p style="color: grey;">Tensei XP VPL</p>
                    <p>
                      <br><br>
                      By using our app, you agree that you have read and understood the terms of use presented here.
                      <br><br>
                      <strong>1 - The Agreement</strong>
                      <br>
                      These terms outline here form an agreement between the user(s) of this VPL ("you") and the Tensei XP VPL group ("us").
                       Any any time of usage, you will be bound to these terms. Please make sure to check out these terms every time a new update is available.
                      <br><br>
                      <strong>2 - Guarantee of Correctness and Liability</strong>
                      <br>
                      There are no known inherent risks associated with the use of this app. However, we will not guarantee that the accuracy and correctness of
                       block functions and other features here will be present. We will also not be held liable for damage resulting from the use of this app,
                       or loss of data on both your side and our side. Please make sure to always back up your data and protect your device from harm and damage.
                      <br><br>
                      <strong>3 - Availability</strong>
                      <br>
                      This app might not be available in the future for various reasons. You agree to accept this possibility.
                      <br><br>
                      <strong>4 - Things you musn't do</strong>
                      You may not copy this program, redistribute it or any derivatives from it, or reverse-engineer it without prior permission from us. You also agree
                       that you will use this program for actions considered legal in your country and everywhere your content will be available in some way. In particular,
                       you may not use this program to further actions which are considered an offense or even criminal under the law.
                      <br><br>
                      <strong>5 - Termination of Use</strong>
                      <br>
                      You can terminate this agreement on your side any time you want by not using this app anymore.
                       However, we may always terminate this agreement with you without prior notification and statement of reasons whatsoever.
                      <br><br>
                      <strong>6 - Legal Disputes</strong>
                      <br>
                      All legal disputes shall be governed under American law. Disputes shall be held in Los Angeles, California.
                      <br><br>
                      <strong>7 - Further Notes</strong>
                      <br>
                      Further rights such as property rights and common law shall apply.
                      <br><br>
                      <strong>8 - Overriding Terms</strong>
                      <br>
                      We do not guarantee that these terms are complete or correct. In case we should send you different terms as written or spoken document via our official email,
                       you agree that the latter shall apply.
                    </p>
                  </q-card-main>
                </q-card>
              </q-popover>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="info" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >Possible Issues</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="warning" size="24px" color="amber" title="Click for more information">
              </q-icon>
              <q-popover>
                <q-card inline style="width: 1000px">
                  <q-card-title>Possible Issues</q-card-title>
                  <q-card-main>
                    <p>
                      <br><br>
                      Depending on the performance of your computer and workload you put onto the program, there might be known issues which you can avoid.
                      <br><br>
                      <strong>Looping Encapsulation/Decapsulation</strong>
                      <br>
                      If you are placing the <strong>Encapsulator</strong> at the coordinates where new blocks will be created, the Encapsulator might loop
                       because both encapsulation and decapsulation will place their conversion output at that position.
                      <br><br>
                      <strong>No Red Border</strong>
                      <br>
                      While you will always see blocks snap together when they are compatible, incompatible blocks won't always be displayed with a red border
                       explicitly. The detection of compatibility works in the positive case, but the display of incompatibility doesn't always work because
                       the red border styling might be overwritten by the ensuing further checks on compatibility with other blocks.
                    </p>
                  </q-card-main>
                </q-card>
              </q-popover>
            </q-item>
          </q-list>
        </q-btn-dropdown>
          <q-btn-dropdown
        color="primary"
        rounded glossy label="Edit"
        icon="edit">
          <q-list link>
             <q-item>
              <q-item-side icon="edit" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >Edit</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" size="24px" color="amber" title="Click for more information">
              </q-icon>
              <q-popover>
                <q-card inline style="width: 1000px">
                  <q-card-title>Edit</q-card-title>
                  <q-card-main>
                    <p>Currently, you can edit everything that is movable. Your browser might also provide some edit functions. Further editing options shall be released in later versions.</p>
                  </q-card-main>
                </q-card>
              </q-popover>
            </q-item>
          </q-list>
        </q-btn-dropdown>
          <q-btn-dropdown
        color="primary"
        rounded glossy label="Window"
        icon="crop_landscape">
          <q-list link>
            <q-item>
              <q-item-side icon="crop_landscape" inverted color="primary" />
              <q-item-main @click.native="openFullscreen">
                <q-item-tile label >Go Fullscreen</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" size="24px" color="amber" title="Click for more information">
                <q-popover>
                  <q-card inline style="width: 500px">
                    <q-card-title>Go Fullscreen</q-card-title>
                    <q-card-main>
                      <p>Makes window fullscreen.</p>
                    </q-card-main>
                  </q-card>
                </q-popover>
              </q-icon>
            </q-item>
            <q-item-separator inset />
            <q-item>
              <q-item-side icon="cancel" inverted color="primary" />
              <q-item-main @click.native="closeFullscreen">
                <q-item-tile label >Exit Fullscreen</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" size="24px" color="amber" title="Click for more information">
                <q-popover>
                  <q-card inline style="width: 500px">
                    <q-card-title>Exit Fullscreen</q-card-title>
                    <q-card-main>
                      <p>Exits fullscreen mode.</p>
                    </q-card-main>
                  </q-card>
                </q-popover>
              </q-icon>
            </q-item>
          </q-list>
        </q-btn-dropdown>
          <q-btn-dropdown
        color="primary"
        rounded glossy label="Tools"
        icon="build">
          <q-list link>
            <q-item>
              <q-item-side icon="code" inverted color="primary" />
              <q-item-main>
                <q-item-tile label >How to Debug</q-item-tile>
              </q-item-main> &nbsp;
              <q-icon name="info" size="24px" color="amber" title="Click for more information">
              </q-icon>
              <q-popover>
                <q-card inline style="width: 500px">
                  <q-card-title>How to Debug</q-card-title>
                  <q-card-main>
                    <p>Press <strong>F12</strong> to open console. Right-click app to view source.
                    </p>
                  </q-card-main>
                </q-card>
              </q-popover>
            </q-item>
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
                      This app is a tool for you to process your images. Just go to the left-hand side
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
                      For more information, check out our <strong>Documentation</strong> under <strong>View</strong> in the menu panel.
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
                    <p style="color: grey;">V 0.21 Last modified: Feb 15, 2019 11:59 pm EST</p>
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
          </q-list>
        </q-btn-dropdown>
      </q-btn-group> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
             <!-- reset to initial state -->
              <q-btn
                class="on-right"
                color="white"
                text-color="blue"
                size="md"
                label="Reset Blocks"
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
          /> &nbsp;
        <q-icon name="info" size="24px" color="amber" title="Click for more information">
        </q-icon>
      </q-item>
    </q-list>
  </q-btn-dropdown> &nbsp;
              <q-btn
                color="indigo"
                glossy
                class="full-width"
                size="lg"
                rounded
                label="Create Loop"
                align="center"
                icon="repeat"
                @click="emit('addBlock', 'forLoop')"
              /> &nbsp;
              <q-btn
                color="blue-grey"
                glossy
                class="full-width"
                size="lg"
                rounded
                label="Toggle Encapsulator"
                align="center"
                icon="branding_watermark"
                @click="emit('toggleEncapsulator')"
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
      leftDrawerOpen: this.$q.platform.is.desktop,
      noFileExists: true
    }
  },
  methods: {
    openURL,
    notImplemented: function () {
      this.emit('notify', 'Not implemented yet.', 'info')
    },
    emit: function (msg, ...args) {
      this.$root.$emit(msg, ...args)
    },
    openFullscreen: function () {
      var elem = document.documentElement
      if (elem.requestFullscreen) {
        elem.requestFullscreen()
      } else if (elem.mozRequestFullScreen) { /* Firefox */
        elem.mozRequestFullScreen()
      } else if (elem.webkitRequestFullscreen) { /* Chrome, Safari and Opera */
        elem.webkitRequestFullscreen()
      } else if (elem.msRequestFullscreen) { /* IE/Edge */
        elem.msRequestFullscreen()
      }
    },
    closeFullscreen: function () {
      if (document.exitFullscreen) {
        document.exitFullscreen()
      } else if (document.mozCancelFullScreen) { /* Firefox */
        document.mozCancelFullScreen()
      } else if (document.webkitExitFullscreen) { /* Chrome, Safari and Opera */
        document.webkitExitFullscreen()
      } else if (document.msExitFullscreen) { /* IE/Edge */
        document.msExitFullscreen()
      }
    },
    checkFileExists: function (message) {
      this.emit('notify', 'Proceeding with' + message, 'info')
      if (this.noFileExists) {
        var element = document.createElement('a')
        element.setAttribute('href', 'data:text/plain;charset=utf-8,' + encodeURIComponent('just some test'))
        element.setAttribute('download', 'userFile001')
        element.style.display = 'none'
        document.body.appendChild(element)
        element.click()
        document.body.removeChild(element)
      }
      this.noFileExists = false
    }
  }
}
</script>
<style>
</style>
