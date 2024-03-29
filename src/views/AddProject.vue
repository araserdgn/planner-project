<template>
  <form action="" @submit.prevent="handleSubmit">
    <label for="">Title</label>
    <input type="text" v-model="title" required> <br><br>

    <label for="">Details</label>
    <textarea v-model="details"></textarea> <br><br>
    <button>Add Project</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title:'',
      details:''
    }
  },
  methods:{
    handleSubmit() {
      let project = {
        title:this.title,
        details: this.details,
        complete : false
      }
      fetch('http://localhost:3000/projects', {
        method:'POST',
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(project)
      }).then(() => this.$router.push('/home')).catch(err => console.log(err))
    }
  }
}
</script>

<style>

form {
  background: floralwhite;
  padding: 20px;
  border-radius: 10px;
}

label {
  display: block;
  color: blueviolet;
  text-transform: uppercase;
  font-size: 14px;
  font-weight: bold;
  letter-spacing: 1px;
  margin: 20px 0 10px 0;
}

input {
  padding: 10px;
  border: 0;
  border-bottom: 2px solid red;
  width: 100%;
  box-sizing: border-box;
}
textarea {
  padding: 10px;
  border-bottom: 2px solid red;
  width: 100%;
  box-sizing: border-box;
  height: 100px;
}

form button {
  display: block;
  margin: 20px auto 0;
  background: lightcoral;
  color: aliceblue;
  padding: 10px;
  border-radius: 7px;
  font-size: 16px;
}

</style>