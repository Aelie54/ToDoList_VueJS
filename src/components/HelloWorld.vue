
<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h4>
      The to do list to organize work & life</h4>

  <form @submit="add(todo)">
    <input type="text" name="title" id="name" placeholder="title" v-model="todo.title" /><br />
    <input type="text" name="description" id="men" placeholder="description" v-model="todo.description"/><br />
    <input type="text" name="deadline" id="size" placeholder="deadline date" v-model="todo.deadline"/><br />
    <input type="text" name="comment" id="price" placeholder="comment" v-model="todo.comment"/><br /><br />
      <input type="submit" value="Add in my to do list" id="submit"/><br /><br />
  </form>
  </div>
</template>

<script>
import { mapState, mapWritableState } from "pinia";
import  { MyList } from "../stores/List";

//mon conteneur d'info pour envoie au store
export default {
  data() {
    return {
      todo: {
        title: "",
        description: "",
        deadline: "",
        comment: "",
      },
    };
  },
  // pour pouvoir ecrire dans mon store et ma liste
  computed: {
    ...mapWritableState(MyList, ["list"]),
  },
  //la fonction qui se lance au moment du submit
  methods: {
    add(todo) {
      console.log(todo);
      let error = "format of your data is not accepted";
      console.log(this.todo.title.length);
      if (
        typeof this.todo.title === "string" &&
        //&& typeof this.todo.title.length >= 0 &&
         this.todo.title !== "" &&
        typeof this.todo.description === "string" &&
        //&& typeof this.todo.description.length >= 0 &&
         this.todo.description !== "" &&
        typeof this.todo.deadline === "string" &&
        //&& typeof this.todo.deadline.length >= 0 &&
         this.todo.deadline !== "" &&
        typeof this.todo.comment === "string" &&
        //&& typeof this.todo.comnent.length >= 0
         this.todo.comment !== ""
      )
      {
        this.list.push(todo);
     }
      return
    },
  },
};
</script>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
