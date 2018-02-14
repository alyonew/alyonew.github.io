<template>
  <div class="drag">
      <div class="to-do">
        <div class="header">TO-DO</div>
        <input v-model="input1" class="name"></input>
        <button id="add1" @click="addNode1">Add card</button>
        <draggable class="drag-area" :list="notes1" :options="{animation:200, group:'dragGroup'}" >
          <div class="card" v-for="(task, index) in notes1">
              {{ task.name }}
          </div>
        </draggable>
      </div>
      <div class="in-progress">
        <div class="header">IN PROGRESS</div>
        <input v-model="input2" class="name"></input>
        <button id="add2" @click="addNode2">Add card</button>
        <draggable class="drag-area" :list="notes2" :options="{animation:200, group:'dragGroup'}">
          <div class="card" v-for="(task, index) in notes2">
              {{ task.name }}
          </div>
        </draggable>
      </div>
      <div class="review-required">
        <div class="header">REVIEW REQUIRED</div>
        <input v-model="input3" class="name"></input>
        <button id="add3" @click="addNode3">Add card</button>
        <draggable class="drag-area" :list="notes3" :options="{animation:200, group:'dragGroup'}" >
          <div class="card" v-for="(task, index) in notes3">
              {{ task.name }}
          </div>
        </draggable>
      </div>
      <div class="done">
        <div class="header">DONE</div>
        <input v-model="input4" class="name"></input>
        <button id="add4" @click="addNode4">Add card</button>
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
      addNode1: function() {
        this.notes1.push({
          name: this.input1
        });
        this.input1 = ''
      },
      addNode2: function() {
        this.notes2.push({
          name: this.input2
        });
        this.input2 = ''
      },
      addNode3: function() {
        this.notes3.push({
          name: this.input3
        });
        this.input3 = ''
      },
      addNode4: function() {
        this.notes4.push({
          name: this.input4
        });
        this.input4 = ''
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
  margin-top: 5px;
  width: 10vw;
  height: 24px;
  border: none;
  cursor: pointer;
  outline: none;
  font-size: 10px;
}
input{
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
  height: 80vh;
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
