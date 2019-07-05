<template>
  <div class="testimonials">
    <div class="container">
      <h1>Testimonials</h1>

      <!-- display area -->
      <el-row :gutter="12">
        <el-col :span="12" v-for="comment in comments">
          <el-card shadow="always">
            <p>
              <strong>{{ comment.name }} - {{ comment.position }}</strong>
            </p>
            <p>{{ comment.comment }}</p>
          </el-card>
        </el-col>
      </el-row>

      <!-- form -->
      <el-form :model="ruleForm" :rules="rules" ref="ruleForm" class="demo-ruleForm">
        <h5>Leave us a Testimonial</h5>
        <!-- name -->
        <el-form-item prop="name" class="form-item">
          <el-input v-model="ruleForm.name" placeholder="Name"></el-input>
        </el-form-item>
        <!-- position -->
        <el-form-item prop="position" class="form-item">
          <el-input v-model="ruleForm.position" placeholder="Position"></el-input>
        </el-form-item>
        <!-- comment -->
        <el-form-item prop="comment" class="form-item">
          <el-input v-model="ruleForm.comment" placeholder="Comment"></el-input>
        </el-form-item>
        <!-- submit -->
        <el-form-item>
          <el-button type="primary" @click="submitForm('ruleForm')">Submit</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
// We will simply need to import axios since it a node package we do not need to specify a file.
import axios from "axios";

export default {
  data() {
    return {
      ruleForm: {
        name: null,
        position: null,
        comment: null
      },
      comments: [],
      // Rules for the form:--------
      // name, position, comment desc can not be empty;
      // name, position title can not more than 30 words, comment desc can not more than 120 words.
      rules: {
        name: [
          { required: true, message: "Please input name", trigger: "blur" },
          { max: 50, message: "Length should be less than 50", trigger: "blur" }
        ],
        position: [
          { required: true, message: "Please input position", trigger: "blur" },
          { max: 50, message: "Length should be less than 50", trigger: "blur" }
        ],
        comment: [
          { required: true, message: "Please input comment", trigger: "blur" },
          {
            max: 120,
            message: "Length should be less than 120",
            trigger: "blur"
          }
        ]
      }
    };
  },
  methods: {
    submitForm(ruleForm) {
      this.$refs[ruleForm].validate(valid => {
        if (valid) {
          let usercomment = {
            name: this.ruleForm.name,
            position: this.ruleForm.position,
            comment: this.ruleForm.comment
          };

          this.comments.push(usercomment);
        } else {
          console.log("error submit!!");
          return false;
        }
      });
      // make an axios put request to send the comments array to firebase
      axios
        .put(
          "https://guo00090-midterm-vue.firebaseio.com/data.json",
          this.comments
        )
        .then(response => {
          // log the status massage on success
          console.log(response);
          console.log("Your data was saved status:" + response.status);
        })
        .catch(error => {
          // we are logging the error message
          console.log("There was an error in saving data: " + error.response);
        });
    }
  },
  // created is a life cycle hook which will run when the instance is created
  created() {
    axios
      // make a GET request using AXIOS to get the data
      .get("https://guo00090-midterm-vue.firebaseio.com/data.json")
      .then(response => {
        console.log(response.data);
        // Checking if the response has some data
        if (response.data) {
          this.comments = response.data;
        }
      })
      .catch(error => {
        console.log("There was an error in getting data: " + error.response);
      });
  }
};
</script>

<style>
h5 {
  padding: 10px 0;
}

.userForm {
  border: 1px solid black;
  padding: 2rem;
}
.el-row {
  margin-bottom: 1rem;
}

.el-card {
  text-align: left;
  margin-bottom: 1rem;
  border-radius: 5px;
  /* background-color: #d5d5d5; */
}

.demo-ruleForm {
  border: solid grey 1px;
  border-radius: 5px;
  /* width: 800px; */
}

.form-item {
  width: 600px;
  margin: 0 auto;
}
</style>