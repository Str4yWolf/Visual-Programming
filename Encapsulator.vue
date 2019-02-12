<template>
  <div class="encapsulator">
    <span style="text-align: center;">
      <br>
      <span style=" padding: 20px;">
        <strong>Encapsu<br> &nbsp; &nbsp; &nbsp; lator</strong>
        <br>
        <q-icon name="info" size="24px" color="yellow" title="Click for more information" style="padding: 10px;">
          <q-popover>
            <q-card inline style="width: 500px">
              <q-card-title>Encapsulator</q-card-title>
              <q-card-main>
                <p>
                  Move a chain of blocks against the Encapsulator and it will generate a single block "<strong>Encapsulation</strong>" from it.
                   Move an Encapsulation block against the Encapsulator and you will get the blocks it contains.
                </p>
              </q-card-main>
            </q-card>
          </q-popover>
        </q-icon>
      </span>
    </span>
  </div>
</template>

<script>
export default {
  // name: 'Binarization',
  data () {
    return {
    }
  },
  methods: {
  }
}
</script>

<style>
div .encapsulator {
  height: 100px;
  width: 100px;
  border: 4px solid black;
  border-radius: 8px;
  background-color: goldenrod;
}
</style>
