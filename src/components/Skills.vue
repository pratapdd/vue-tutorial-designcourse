<template>
  <div class="hello">
    <div class="holder">

      <form @submit.prevent="addSkill">
        <input type="text" placeholder="Enter a skill you have..." v-model="skill" v-validate="'min:5'" name="skill">
        
        <transition name="alert-in" enter-active-class="animated flipInX" leave-active-class="animated flipOutX">
          <p class="alert" v-if="errors.has('skill')">{{ errors.first('skill') }}</p>
        </transition>
        <!-- <input type="checkbox" id="checkbox" v-model="checked"> -->
      </form>

      <ul>
        <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
          <li v-for="(data, index) in skills" :key='index'>
            {{ data.skill }}
            <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
          
          </li>
        </transition-group>
      </ul>

      <p>These are the skills that you possess.</p>

      <!-- another-classv-if and v-else -->
      <!--  <p v-if="skills.length >= 1">You have more than one skills.</p> -->
      <!-- <p v-else>You have less than or equal to 1 skill</p> -->

      <!-- v-bind:class for single class and multiple class -->
      <!-- <div v-bind:class="{ alert: showAlert, 'another-class': showClass }"></div> -->

      <!-- v-bind:class for object -->
      <!-- <div v-bind:class="alertObject"></div> -->

      <!-- v-bind:style directive  -->
      <!-- <div v-bind:style="{ backgroundColor: bgColor, width: bgWidth, height: bgHeight }"></div> -->

    </div>


    <!-- {{ name }} -->

    <!-- {{ btnState ? 'The button is disable' : 'The button is active' }} -->

    <!-- <button v-on:click="changeName" v-bind:disabled="btnState">Change Name</button> -->
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      // checked: false,
      skill: '',
      // name: 'Coursetro',
      // btnState: false,
      // changeName() {
      //   alert('I am changed')
      // }
      skills: [
        { "skill": "Vue.js" },
        { "skill": "Frontend Developer" }
      ],
      // showAlert: true,
      // showClass: true
      // alertObject: {
      //   alert: true,
      //   'another-class': true
      // }
      // bgColor: 'yellow',
      // bgWidth: '100%',
      // bgHeight: '30px'
    }
  },
  methods: {
    addSkill() {
      this.$validator.validateAll().then((result) => {
        if (result) {
          this.skills.push({skill: this.skill})
          this.skill = '';
        } else {
          /* eslint-disable */
          console.log('Not valid');
        }
      })
    },
    remove(id) {
      this.skills.splice(id,1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

@import "https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.7.0/animate.css";

@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css"; 
  /* .alert {
    background-color: yellow;
    width: 100%;
    height: 30px;
  }
  .another-class {
    border: solid 2px black;
  } */

  .holder {
    background: #fff;
  }

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

  p {
    text-align: center;
    padding: 30px 0;
    color: gray;
  }

  .container {
    box-shadow: 0px 0px 40px lightgray;
  }

  input {
    width: calc(100% - 40px);
    border: 0;
    padding: 20px;
    font-size: 1.3em;
    background-color: #323333;
    color: #687F7F;
  }

  .alert {
    background: #fdf2ce;
    font-weight: bold;
    display: inline-block;
    padding: 5px;
    margin-top: -20px;
  }

  .alert-in-enter-active {
    animation: bounce-in .5s;
  }

  .alert-in-leave-active {
    animation: bounce-in .5s reverse;
  }


  @keyframes bounce-in {
    0% {
      transform: scale(0);
    }
    50% {
      transform: scale(1.5);
    }
    100% {
      transform: scale(1);
    }
  }

  i {
    float: right;
    cursor: pointer;
  }


</style>
