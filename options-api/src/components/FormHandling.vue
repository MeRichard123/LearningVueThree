<template>
  <button @click="showing = !showing">Toggle Form</button>
  <div v-show="showing">
    <h1>Form Handling!!</h1>
    <!-- Equivalent to calling preventDefault on the event -->
    <form action="" @submit.prevent="submitForm">
      <pre>{{ JSON.stringify(formValues, null, 2) }}</pre>
      <div>
        <label for="name">Name</label>
        <!-- V-model can send data to the script by binding it -->
        <!-- This will bind to the name data attribute: Two way binding -->
        <input type="text" id="name" v-model.trim.lazy="formValues.name" />
        <!-- Modifiers allow us to perform actions in the template -->
        <!-- .trim removes whitespace -->
        <!-- .lazy bind on focus lost rather than each keystroke -->
      </div>
      <div>
        <label for="profile">Profile Summary</label>
        <textarea
          name=""
          id="profile"
          v-model="formValues.profileSummary"
        ></textarea>
      </div>
      <div>
        <!-- If we wanted to submit the form when you click a key in the age field -->
        <label for="age">Age</label>
        <!-- Modifier to make sure a number is entered -->
        <input
          @keyup.enter="submitForm"
          type="number"
          id="age"
          v-model.number="formValues.age"
        />
      </div>
      <div>
        <label for="country">Country</label>
        <select name="" id="country" v-model="formValues.country">
          <option value="">Select A country</option>
          <option value="India">India</option>
          <option value="Vietnam">Vietnam</option>
          <option value="Singapore">Singapore</option>
        </select>
      </div>
      <div>
        <label for="loc">Job Location:</label>
        <select name="" id="loc" v-model="formValues.jobLocation" multiple>
          <option value="India">India</option>
          <option value="Vietnam">Vietnam</option>
          <option value="Singapore">Singapore</option>
        </select>
      </div>
      <div>
        <input
          type="checkbox"
          name=""
          id="remotework"
          v-model="formValues.remoteWork"
          true-value="yes"
          false-value="no"
        />
        <label for="remotework">Open to remote work?</label>
      </div>
      <div>
        <label for="">Skill set</label>
        <input
          type="checkbox"
          id="html"
          value="html"
          v-model="formValues.skillSet"
        />
        <label for="html">HTML</label>

        <input
          type="checkbox"
          id="js"
          value="js"
          v-model="formValues.skillSet"
        />
        <label for="js">Javascript</label>
        <input
          type="checkbox"
          id="css"
          value="css"
          v-model="formValues.skillSet"
        />
        <label for="css">CSS</label>
      </div>
      <div>
        <label>Years of Experience</label>
        <input
          type="radio"
          id="0-2"
          value="0-2"
          v-model="formValues.yearsOfExperience"
        />
        <label for="0-2">0-2</label>
        <input
          type="radio"
          id="3-5"
          value="3-5"
          v-model="formValues.yearsOfExperience"
        />
        <label for="3-5">3-5</label>
        <input
          type="radio"
          id="6-10"
          value="6-10"
          v-model="formValues.yearsOfExperience"
        />
        <label for="6-10">6-10</label>
        <input
          type="radio"
          id="10+"
          value="10+"
          v-model="formValues.yearsOfExperience"
        />
        <label for="10+">10+</label>
      </div>
      <!-- Submit Form -->
      <div>
        <button type="submit">Send Form</button>
      </div>
    </form>
  </div>
</template>
<script>
export default {
  name: "FormHandling",
  data() {
    return {
      formValues: {
        name: "",
        profileSummary: "",
        country: "",
        jobLocation: [],
        remoteWork: "no",
        skillSet: [],
        yearsOfExperience: "",
        age: null,
      },
      showing: false,
    };
  },
  methods: {
    submitForm() {
      console.log("Form Values", this.formValues);
    },
  },
};
</script>
<style>
form {
  text-align: center;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
}
form div {
  margin: 5px;
}
label {
  font-weight: bold;
  display: flex;
  margin-bottom: 5px;
}
input + label {
  font-weight: bold;
  display: inline-flex;
  margin-right: 20px;
}
input[type="text"],
textarea,
select {
  display: block;
  width: 400px;
  padding: 6px 12px;
  font-size: 14px;
  line-height: 1.42857143;
  color: #555;
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 4px;
}
</style>
