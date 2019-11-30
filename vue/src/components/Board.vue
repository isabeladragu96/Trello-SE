<template>
  <div class="col-md-3">
    <b-card
    :title= "board.board_name"
    :img-src="'https://picsum.photos/600/300/?image=' + Math.floor(Math.random() * 100)"
    img-alt="Image"
    img-top
    tag="article"
    style="max-width: 20rem; margin-top: 30px; margin-left:20px; margin-right:10px;"
    class="mb-2"
    >
      <b-button href="#" variant="default" style="font-weight:bold">Show details</b-button>
      <b-button v-b-modal="'modal-' + board._id" class="mx-1" variant="default">Settings</b-button>
    </b-card>
    <b-modal :id="'modal-' + board._id" :title="board.board_name + ' settings'" hide-footer>
      <div class="text-center">
        <b-input-group prepend="Edit board's name" class="my-3">
          <b-form-input></b-form-input>
          <b-input-group-append>
            <b-button variant="dark">Save</b-button>
          </b-input-group-append>
        </b-input-group>
        <b-button variant="warning" @click="deleteBoard(board._id)">Delete</b-button>
      </div>
    </b-modal>
  </div>
</template>

<script>
export default {
  name: 'Board',
  props:  { 
    board: Object
  },
  methods: {
    deleteBoard: function(board_id) {
      this.$emit("deleteBoard", board_id)
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
