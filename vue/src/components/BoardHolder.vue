<template>
  <div class="row">
    <Board @deleteBoard = "onBoardDelete"
    v-for="board in boards"
    :key="board._id"
    :board="board"
    />
  </div>
</template>

<script>
import axios from "axios";
import Board from "./Board.vue";

export default {
  name: 'BoardHolder',
  data: function() {
    return { 
      boards: [],
      error: null
    }
  },
  created: function() {
    axios.get('http://localhost:3000/boards')
      .then(response => {
        this.boards = response.data.boards;
      })
      .catch(error => {
        this.error = error;
      });
  }, 
  components: {
    Board
  },
  methods: {
    onBoardDelete: function(id) {
      axios
        .delete("http://localhost:3000/boards/" + id)
        .then(res => {
          this.boards = this.boards.filter(function(board) {
            return board._id != res.data._id;
          });
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
