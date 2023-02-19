<template>
  <div class="container">
    <div class="holder">
      <ul>
        <div v-for="(skill, index) in skillset" :key="index" class="skill-container">
          <li>{{ index + 1 }}. {{ skill }}</li>
          <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
        </div>
        <form @submit.prevent="addskillset">
          <div class="skill-container">
            <input type="text" placeholder="Enter new skill here..." v-model="newSkill" @keydown.enter="addskillset">
            <button type="submit"><i class="fa fa-plus"></i></button>
          </div>
        </form>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Skills-List',
  data() {
    return {
      skillset: [
        'Vue.js',
        'Front End Developer',
        'Python',
      ],
      newSkill: ''
    }
  },
  methods: {
    addskillset: function () {
      if (this.newSkill) {
        this.skillset.push(this.newSkill);
        this.newSkill = "";
      }
    },
    remove: function (id) {
      this.skillset.splice(id, 1);
    }
  }
}
</script>

<style scoped>
@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css";
@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";

.holder { background: #fff; }

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

ul li {
  padding: 20px;
  font-size: 1.3em;
  background-color: #E0EDF4;
  border-left: 5px solid #3EB3F6;
  margin-bottom: 2px;
  color: #3E5252;
}

.skill-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 10px;
}

input {
  width: calc(100% - 40px);
  border: 0;
  padding: 20px;
  font-size: 1.3em;
  background-color: #323333;
  color: #687F7F;
}

button {
  border: 0;
  padding: 0 10px;
  background-color: #3EB3F6;
  color: #fff;
  font-size: 1.3em;
  cursor: pointer;
}

i {
  cursor: pointer;
}
</style>