<template>
  <div class="drag">
    <input v-model="input" class="name"></input>
    <button id="add" @click="addNode">Add new task</button>
      <div class="to-do">
        <div class="header">TO-DO</div>
        <draggable class="drag-area" :list="notes1" :options="{animation:200, group:'dragGroup'}" >
          <div class="card" v-for="(task, index) in notes1">
              {{ task.name }}
          </div>
        </draggable>
      </div>
      <div class="in-progress">
        <div class="header">IN PROGRESS</div>
        <draggable class="drag-area" :list="notes2" :options="{animation:200, group:'dragGroup'}">
          <div class="card" v-for="(task, index) in notes2">
              {{ task.name }}
          </div>
        </draggable>
      </div>
      <div class="review-required">
        <div class="header">REVIEW REQUIRED</div>
        <draggable class="drag-area" :list="notes3" :options="{animation:200, group:'dragGroup'}" >
          <div class="card" v-for="(task, index) in notes3">
              {{ task.name }}
          </div>
        </draggable>
      </div>
      <div class="done">
        <div class="header">DONE</div>
        <draggable class="drag-area" :list="notes4" :options="{animation:200, group:'dragGroup'}" >
          <div class="card" v-for="(task, index) in notes4">
              {{ task.name }}
          </div>
        </draggable>
      </div>
    </div>

</template>

<script>
  import draggable from 'vuedraggable';
  export default {
    components: {
      draggable
    },
    name: 'app',
    data () {
      return {
        notes1: [],
        notes2: [],
        notes3: [],
        notes4: [],
      }
    },

    methods: {
      addNode: function() {
        this.notes1.push({
          name: this.input
        });
        this.input = ''
      },

    }
  }
</script>



<style>
.drag {
  font-family: Roboto;
  text-align: center;
}
button {
  width: 10vw;
  height: 24px;
  border: none;
  cursor: pointer;
  outline: none;
  font-size: 10px;
}
input{
  margin-left: 20vw;
  margin-top: 5vh;
  margin-bottom: 5vh;
  width: 50vw;
  height: 20px;
  border: 1px solid #CCC;
}

.card {
  color: #000;
  background-color: #CCC;
  height: auto;
  min-height: 40px;
  text-align: center;
  margin-left: 3%;
  margin-right: 3%;
  margin-top: 5%;
  cursor: move;
}

.drag-area
{
  float: left;
  height: 100vh;
  width: 24vw;
}

.to-do
{
  float: left;
  height: 100vh;
  width: 24vw;
  border: 1px solid #CCC;
}

.in-progress
{
  float: left;
  height: 100vh;
  width: 24vw;
  border: 1px solid #CCC;
}

.review-required
{
  float: left;
  height: 100vh;
  width: 24vw;
  border: 1px solid #CCC;
}

.done
{
  float: left;
  height: 100vh;
  width: 24vw;
  border: 1px solid #CCC;
}

.header {
  margin-top: 5%;
  margin-bottom: 5%;
}
</style>
