<template>
    <div class="div">
        
        <h3>Edit Form ID number: {{ this.id }}</h3>
        <form @submit.prevent="handleSubmit">
            <label for="">Title</label>
            <input type="text" v-model="title" required /> <br /><br />
    
            <label for="">Details</label>
            <textarea v-model="details"></textarea> <br /><br />
            <button>Add Project</button>
        </form>

    </div>
</template>

<script>
export default {
    props:['id'],
    data() {
        return {
            title:"",
            details:"",
            uri:'http://localhost:3000/projects/' + this.id
        }
    },
    mounted() {
        fetch(this.uri).then(res => res.json()).then(data => {
            this.title = data.title,
            this.details = data.details
        })
    },
    methods: {
        handleSubmit() {
            fetch(this.uri, {
                method: 'PATCH',
                headers: {"Content-Type":"application/json"},
                body: JSON.stringify({title:this.title, details : this.details})
            })
            .then(()=>this.$router.push('/home'))
            .catch((err) => console.log(err))
        }
    }
};
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
.div h3 {
    text-align: center;
}
</style>

