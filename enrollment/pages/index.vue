<template>
  <body>
      <div class="login">
        <div class="login-screen">
          <div class="app-title">
            <h1>Login</h1>
          </div>

          <div class="login-form">
            <div class="control-group">
              <input type="text" class="login-field" value="" placeholder="Username" id="login-name">
              <label class="login-field-icon fui-user" for="login-name"></label>
            </div>

            <div class="control-group">
              <input type="password" class="login-field" value="" placeholder="Password" id="login-pass">
              <label class="login-field-icon fui-lock" for="login-pass"></label>
            </div>

            <a class="btn btn-primary btn-large btn-block" href="#">login</a>
            <a class="login-link" href="#">Forget password?</a>
          </div>
        </div>
      </div>
  </body>
</template>

<script>
export default {
  name: 'IndexPage',
}
</script>

<style scoped>
  * {
  box-sizing: border-box;
  }

  *:focus {
    outline: none;
  }

  .login {
  margin: 250px auto;
  width: 350px;
  }

  .app-title {
  margin: 10px auto;
  text-align: center;
  color: #ef3636;
  }

  .login-form {
  text-align: center;
  border-color: #ef3636;
  border-width: 10px;
  }

  input {
  text-align: center;
  background-color: #ff303038;
  border: 2px solid transparent;
  border-radius: 3px;
  font-size: 16px;
  font-weight: 200;
  padding: 10px 0;
  width: 350px;
  transition: border .5s;
  }

  input:focus {
  border: 2px solid #ef3636;
  box-shadow: none;
  }

  .btn {
    border: 2px solid transparent;
    background: #ef3636;
    color: #FFF;
    font-size: 16px;
    line-height: 25px;
    padding: 10px 0;
    text-decoration: none;
    text-shadow: none;
    border-radius: 3px;
    box-shadow: none;
    transition: 0.25s;
    display: block;
    width: 350px;
    margin: 0 auto;
  }

  .btn:hover {
    background-color: #ef363679;
  }

  .login-link {
    font-size: 12px;
    color: #444;
    display: block;
    margin-top: 12px;
  }
</style>