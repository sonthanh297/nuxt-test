<!-- <template>
    <div>
        <h1>Login Page</h1>
        <Login />
        <button @click="redirectToRegister">Đăng ký</button>
    </div>
</template>

<script>
import Login from '~/components/Login.vue'
import RegisterButton from '~/components/RegisterButton.vue'

export default {
    components: {
        Login,
        RegisterButton
    },
    methods: {
        redirectToRegister() {
            this.$router.push('/register')
        }
    }
}
</script> -->
<!-- <template>
    <div class="login-page">
        <div class="login-form">
            <h1>Đăng nhập</h1>
            <form @submit="login">
                <div class="form-group">
                    <label for="username">Tên đăng nhập:</label>
                    <input type="text" id="username" v-model="username" required>
                </div>
                <div class="form-group">
                    <label for="password">Mật khẩu:</label>
                    <input type="password" id="password" v-model="password" required>
                </div>
                <div class="button-group">
                    <button type="submit" class="btn btn-primary">Đăng nhập</button>
                    <nuxt-link to="/register" class="btn btn-secondary">Đăng ký</nuxt-link>
                    <router-link to="/photo" class="btn btn-secondary">Photo</router-link>
                    <button @click="handleButtonClick">Click me</button>
                </div>
            </form>
        </div>
    </div>
</template> -->

<template>
    <div>
      <form @submit.prevent="register">
        <div class="mb-3">
          <label for="fullname" class="form-label">Full Name</label>
          <input
            type="text"
            v-model="registerData.fullname"
            class="form-control"
            id="fullname"
          />
        </div>
        <div class="mb-3">
          <label for="email" class="form-label">Email address</label>
          <input
            type="email"
            class="form-control"
            id="email"
            v-model="registerData.email"
            aria-describedby="emailHelp"
          />
        </div>
        <div class="mb-3">
          <label for="password" class="form-label">Password</label>
          <input
            type="password"
            v-model="registerData.password"
            class="form-control"
            id="password"
          />
        </div>
        <button type="submit" class="btn btn-primary w-100">Register</button>
      </form>
    </div>
  </template>

<script>
export default {
  data() {
    return {
      registerData: {
        fullname: "",
        email: "",
        password: ""
      }
    };
  },
  methods: {
    async register() {
      try {
        const response = await this.$axios.post('/api/login2', {
                    username: this.registerData.fullname,
                    password: this.registerData.password
                });
        console.log(response);
        this.$router.push('/photo');
      } catch (err) {
        console.log(err);
      }
    }
  }
};
</script>

<!-- <script>
export default {
    data() {
        return {
            username: '',
            password: ''
        }
    },
    methods: {
        async login() {
            //  this.$router.push('/photo');
            try {
                //this.$router.push('/photo');
                console.log("call log");
                // const response = await this.$axios.post('/api/login2', {
                //     username: this.username,
                //     password: this.password
                // });

                // await this.$axios.$post('/login').then(rs => {
                //     console.log("call log", rs);
                // }
                // )

                const data = await this.$axios.get(`/images`).catch(() => ({ success: false }))

                console.log(data);
              //  console.log("call log", response);
              //  const token = response.data.token;
                //localStorage.setItem('token', token); // Lưu token vào localStorage
              //  console.log('Đăng nhập thành công:', token);
                // Chuyển đến màn hình photo
               // this.$router.push('/photo');
                //this.$router.push({name: 'photo'});
             //   console.log('Đăng nhập thành công:', token);
            } catch (error) {
                console.error('Đăng nhập thất bại:', error.response.data.message);
            }
        },

        async handleButtonClick() {
            const response = await this.$axios.post('/api/login2', {
                    username: "1",
                    password: "1"
                });
                const token = response.data.token;
                localStorage.setItem('token', token);
           // const data = await this.$axios.get(`/images`).catch(() => ({ success: false }))
            // Code to be executed when the button is clicked
            console.log(response);
            this.$router.push('/photo');
        }
    }
}
</script> -->

<style scoped>
.login-page {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #f5f5f5;
}

.login-form {
    max-width: 400px;
    padding: 20px;
    background-color: #fff;
    border-radius: 4px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.form-group {
    margin-bottom: 20px;
}

label {
    font-weight: bold;
}

input[type="text"],
input[type="password"] {
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
}

.button-group {
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.btn-primary {
    background-color: #007bff;
    color: #fff;
    border: none;
}

.btn-primary:hover {
    background-color: #0069d9;
}

.btn-secondary {
    background-color: #6c757d;
    color: #fff;
    border: none;
}

.btn-secondary:hover {
    background-color: #5a6268;
}

h1 {
    text-align: center;
    margin-bottom: 20px;
}
</style>
