<template>
  <b-container fluid class="mg-5">
    <b-row>
      <b-col style="padding:0">
        <b-form-input id="input"
                      v-model="title"
                      type="text"
                      placeholder="Title"
                      size="sm" class="width-100 text-14 bold"
                      required></b-form-input>
        <br>
        <b-form-textarea
            id="textarea"
            v-model="text" class="height-70-vh"
            placeholder="Note"
            no-resize
        ></b-form-textarea>
        <br>
      </b-col>
      <b-button block variant="outline-success" @click="saveNote">Save note</b-button>
    </b-row>
  </b-container>
</template>

<script>
import {BFormTextarea, BButton, BFormInput} from 'bootstrap-vue';

export default {
  name: "NewNote",
  components: {
    BFormTextarea,
    BButton,
    BFormInput
  },
  props:['edit','id'],
  data() {
    return {
      title: ''
    }
  },
  computed:{
    text: function () {
      if (this.$props.edit)
        return "//TODO get text for edit "+this.$props.id
      else return "";
    }
  },
  methods: {
    saveNote: function () {
    alert("//TODO save note with title "+this.title)
    }
  }
}
</script>

<style scoped>
.text-14 {
  font-size: 16px;
  font-family: Helvetica;
}

.bold {
  font-weight: bold;
}

.height-70-vh {
  height: 70vh;
}
</style>