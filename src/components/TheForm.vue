<template>
  <form @submit.prevent="handleSubmit">
    <div
      class="form-control"
      :class="{ invalid: userNameStatus === 'invalid' }"
    >
      <label for="user-name">Your Name</label>
      <input
        v-model.trim="userName"
        @blur="validateInput"
        id="user-name"
        name="user-name"
        type="text"
      />
      <p v-if="userNameStatus === 'invalid'">Pease enter a valid name.</p>
    </div>
    <div class="form-control">
      <label for="age">Your Age (Years)</label>
      <input v-model="userAge" id="age" name="age" type="number" />
    </div>
    <div class="form-control">
      <label for="referrer">How did you hear about us?</label>
      <select v-model="referrer" id="referrer" name="referrer">
        <option value="google">Google</option>
        <option value="wom">Word of mouth</option>
        <option value="newspaper">Newspaper</option>
      </select>
    </div>
    <div class="form-control">
      <h2>What are you interested in?</h2>
      <div>
        <input
          v-model="interest"
          value="news"
          id="interest-news"
          name="interest"
          type="checkbox"
        />
        <label for="interest-news">News</label>
      </div>
      <div>
        <input
          v-model="interest"
          value="tutorials"
          id="interest-tutorials"
          name="interest"
          type="checkbox"
        />
        <label for="interest-tutorials">Tutorials</label>
      </div>
      <div>
        <input
          v-model="interest"
          value="nothing"
          id="interest-nothing"
          name="interest"
          type="checkbox"
        />
        <label for="interest-nothing">Nothing</label>
      </div>
    </div>
    <div class="form-control">
      <h2>How do you learn?</h2>
      <div>
        <input
          v-model="how"
          value="video"
          id="how-video"
          name="how"
          type="radio"
        />
        <label for="how-video">Video Courses</label>
      </div>
      <div>
        <input
          v-model="how"
          value="blogs"
          id="how-blogs"
          name="how"
          type="radio"
        />
        <label for="how-blogs">Blogs</label>
      </div>
      <div>
        <input
          v-model="how"
          value="other"
          id="how-other"
          name="how"
          type="radio"
        />
        <label for="how-other">Other</label>
      </div>
    </div>
    <div class="form-control">
      <rating-control></rating-control>
    </div>
    <div class="form-control">
      <input v-model="confirm" type="checkbox" id="terms" name="terms" />
      <label for="terms">Agree to terms and conditions?</label>
    </div>
    <div>
      <button>Save Data</button>
    </div>
  </form>
</template>

<script>
import RatingControl from './rating/RatingControl.vue';
export default {
  data() {
    return {
      userName: '',
      userNameStatus: 'pending',
      userAge: null,
      referrer: 'wom',
      interest: [],
      how: null,
      confirm: false,
    };
  },
  methods: {
    handleSubmit() {
      console.log('username: ' + this.userName);
      console.log('userAge: ');
      console.log(this.userAge);
      console.log('referrer: ' + this.referrer);
      console.log('checkbox:' + this.interest);
      console.log('radio: ' + this.how);
      console.log('confirm: ' + this.confirm);
      this.userName = '';
      this.userAge = null;
      this.referrer = 'wom';
      this.interest = [];
      this.how = null;
      this.confirm = false;
    },
    validateInput() {
      if (this.userName === '') {
        this.userNameStatus = 'invalid';
      } else {
        this.userNameStatus = 'valid';
      }
    },
  },
  components: { RatingControl },
};
</script>

<style scoped>
form {
  margin: 2rem auto;
  max-width: 40rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 2rem;
  background-color: #ffffff;
}

.form-control {
  margin: 0.5rem 0;
}

.form-control.invalid input {
  border-color: red;
}

.form-control.invalid label {
  color: red;
}

label {
  font-weight: bold;
}

h2 {
  font-size: 1rem;
  margin: 0.5rem 0;
}

input,
select {
  display: block;
  width: 100%;
  font: inherit;
  margin-top: 0.5rem;
}

select {
  width: auto;
}

input[type='checkbox'],
input[type='radio'] {
  display: inline-block;
  width: auto;
  margin-right: 1rem;
}

input[type='checkbox'] + label,
input[type='radio'] + label {
  font-weight: normal;
}

button {
  font: inherit;
  border: 1px solid #0076bb;
  background-color: #0076bb;
  color: white;
  cursor: pointer;
  padding: 0.75rem 2rem;
  border-radius: 30px;
}

button:hover,
button:active {
  border-color: #002350;
  background-color: #002350;
}
</style>
