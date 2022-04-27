<template>
  <b-container>
    <b-row>
      <b-col  class="max-width">
        <b-container text-align="left">
          <b-row>
            <b-button block variant="success" @click="newNote">New note</b-button>
          </b-row><br>
          <b-row>

            <li v-for="item in items" :key="item.message">
              {{ item.message }}
            </li>

            <b-button block variant="light" class="text-left" @click="editNote(t.id)" v-for="t in titles" :key="t.id">{{t.title}}</b-button>
          </b-row>
        </b-container>
        <br>
      </b-col>
      <b-col  class="max-width">
        <NewNote :edit="editBind" :id="editId"/>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import NewNote from './NewNote.vue'
export default {
  name: "Notebook",
  components: {
    NewNote
  },
  data() {
    return {
      editBind: false,
      editId:null
    }
  },
  computed:{
    titles: function () {
      return [{title:"title1",id:1},{title:"title2",id:2},{title:"title3",id:3},
        {id:4,title:"AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA"}]
    }
  },
  methods: {
    newNote: function () {
      this.editBind = false;
    }, editNote: function (id) {
      this.editBind = true;
      this.editId=id;
    }
  }
}
</script>

<style scoped>
.max-width{
  max-width: 50% !important;
}
.text-left{
  text-align: left;
  word-wrap: break-word !important;
}
</style>