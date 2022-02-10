<template>
  <div>
    <h3>Mis paneles</h3>
    <div class="boards-collection">
      <input
        type="text"
        placeholder="Añade un nuevo panel"
        v-model="boardName"
        @keyup.enter="addBoard()"
      />
      <BoardCard
        v-for="(board, index) in boards"
        :key="index"
        :name="board.name"
        :id="board.id"
      ></BoardCard>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import BoardCard from "@/components/BoardCard";

export default {
  name: "Home",
  components: { BoardCard },
  data() {
    return {
      boardName: "",
      boards: [
        {
          id: 1,
          name: "Tareas",
        },
        {
          id: 2,
          name: "Lista de las compras",
        },
      ],
    };
  },
  methods: {
    addBoard() {
      this.boards.push({ name: this.boardName });
      this.boardName = "";
    },
  },
};
</script>

<style lang="scss" scoped>
h3 {
  text-align: left;
  margin: 1.5rem;
}
.boards-collection {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  padding-top: 1rem;
}
input {
  box-sizing: border-box;
  background-color: #546e7a;
  border: 2px solid #546e7a;
  border-radius: 3px;
  font-size: 1.1rem;
  outline: 0;
  padding: 0.5rem;
  transition: all 600ms ease;
  &:focus,
  &:active {
    background-color: white;
    color: #546e7a;
  }
  &::placeholder {
    color: white;
  }
}
</style>
