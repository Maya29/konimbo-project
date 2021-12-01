<template>
   
 
    <form @submit="onSubmit" class="add-form">
       <div><h3>
         טופס</h3></div>
    <div class="form-control">
      <label>שם</label>
      <input type="text" v-model="fName" name="fName" placeholder="שם" />
    </div>
    <div class="form-control">
      <label>אמייל</label>
      <input
        type="email"
        v-model="fEmail"
        name="fEmail"
        placeholder="אמייל"
      />
    </div>
      <div class="form-control">
      <label>טלפון</label>
      <input type="number" v-model="fPhone" name="fPhone" placeholder="טלפון" />
    </div>

    <input type="submit" value="שלח" class="btn btn-block" />
  </form>
</template>

<script>
export default {
    name: "SendForm",
data() {
    return {
      fName: '',
      fEmail: '',
      fPhone: '',
    }
  },
  
  methods: {
    onSubmit(e) {
      e.preventDefault()
      if (!this.fName || !this.fEmail || !this.fPhone) {
        alert('יש למלות את ל הפרטים')
        return
      }
      const newForm = {
        name: this.fName,
        email:  this.fEmail,
        phone:  this.fPhone,
      }
      this.sendForm(newForm)
          this.fName = ''
      this.fEmail = ''
      this.fPhone = ''
    },
     async sendForm(newForm) {
      const res = await fetch('http://webhook.site/138cecf3-585c-45a1-b6b7-91824aa7859e', {
        method: 'POST',
        mode: "no-cors",
        headers: {
         "Access-Control-Allow-Origin": "*",
         'Content-Type': 'application/json',
        },
        body: JSON.stringify(newForm),
      })
    }
  },
}
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
  direction: rtl;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
.btn {
  display: inline-block;
  background: blue;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn-block {
  display: block;
  width: 100%;
}
</style>

