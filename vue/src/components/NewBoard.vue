<template>
  <div class="col-md-3">
    <b-card
    img-src="https://www.placecage.com/640/360"
    img-alt="Image"
    img-top
    tag="article"
    style="max-width: 20rem; margin-top: 30px; margin-left:20px; margin-right:10px;"
    class="mb-2"
    >
      <b-button v-b-modal.newBoard class="mx-1" variant="default" style="font-weight:bold">Add new board</b-button>
    </b-card>

    <b-modal hide-footer id="newBoard">
      <div class="text-center">
        <b-input-group prepend="New board's name" class="my-3">
          <b-form-input v-model="newBoardName"></b-form-input>
          <b-input-group-append>
            <b-button variant="dark" @click="saveNewBoard">Save</b-button>
          </b-input-group-append>
        </b-input-group>
      </div>
    </b-modal>

  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'NewBoard',
  data: function() {
    return {
      newBoardName: ""
    }
  },
  methods: {
    saveNewBoard: function() {
      axios.post('http://localhost:3000/boards', {
        newBoardName: this.newBoardName
      })
      .then(res => {
          this.$emit("addBoard", res.data.board);

          this.$bvModal.hide("newBoard");
          this.newBoardName = "";
        })
        .catch(err => {
          this.err = err;
        });
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
