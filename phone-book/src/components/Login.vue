<template>
 <div>
  <h2>Login</h2>
   <form v-on:submit='login'>
   <label for='emile'>email</label>
   <input type='text' name='email' id='emile'/><br>
   <label for='pass'>pass</label>
   <input type='password' name='password'  id='pass'/><br>
    <input type='submit' value='Login' />
   </form>
 </div>
</template>
<script>
import router from '../router'
import axios from 'axios'
export default {
  name: 'Login',
  methods: {
    login: (e) => {
      e.preventDefault()
      let email = 'user@email.com'
      let password = 'password'
      let login = () => {
        let data = {
          email: email,
          password: password
        }
        axios.post('/api/login', data)
          .then((response) => {
            console.log('Logged in')
            router.push('/dashboard')
          })
          .catch((errors) => {
            console.log('Cannot log in')
          })
      }
      login()
    }
  }
}
</script>
