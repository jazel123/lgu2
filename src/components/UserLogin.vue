<template>
  <div class="container">
    <div class="description">
      <h1>Welcome to LGU Cordova</h1>
      <p>
        The Attendance and Leave Tracker helps manage and monitor attendance and leave requests efficiently.
        Designed specifically for local government units, it streamlines the process, making it easy for employees
        and administrators to handle attendance records and leave requests.
      </p>
    </div>
    <div class="form-container" v-if="showForm">
      <h2>Login</h2>
      <form @submit.prevent="handleLogin">
        <div class="form-group">
          <label for="email">Email:</label>
          <input type="email" id="email" v-model="email" required />
        </div>
        <div class="form-group">
          <label for="password">Password:</label>
          <input type="password" id="password" v-model="password" required />
        </div>
        <button type="submit">Login</button>
      </form>
      <p>Don't have an account? <router-link to="/register" class="register-link">Register here</router-link></p>
    </div>
    <button v-if="!showForm" @click="showForm = true" class="show-form-button">Show Login Form</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showForm: false,
      email: '',
      password: '',
    };
  },
  methods: {
    handleLogin() {
      console.log('Login Attempted', this.email, this.password);
      
      if (this.email === 'admin@gmail.com') {
        // Redirect to admin dashboard
        this.$router.push('/admin-dashboard');
      } else {
        // Redirect to user dashboard
        this.$router.push('/dashboard');
      }
    },
  },
};
</script>


<style scoped>
.container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f0f0f0;
  padding: 0 2rem;
  box-sizing: border-box;
}

.description {
  text-align: left;
  color: #333;
  max-width: 500px;
  margin-right: 10rem;
}

.description h1 {
  font-size: 2rem;
  margin-bottom: 1rem;
  color: #007bff;
}

.description p {
  font-size: 1rem;
  margin-left: 10px;
}

.form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background: rgba(255, 255, 255, 0.8);
  padding: 2rem;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  width: 100%;
  max-width: 400px;
  text-align: center;
  box-sizing: border-box;
}

h2 {
  margin-bottom: 1rem;
  color: #007bff;
}

.form-group {
  margin-bottom: 1rem;
  width: 100%;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
}

.form-group input {
  width: 100%;
  padding: 0.5rem;
  border: 1px solid #ddd;
  border-radius: 4px;
}

button {
  width: 100%;
  padding: 0.75rem;
  background-color: #28a745;
  border: none;
  color: white;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #218838;
}

.register-link {
  color: #007bff;
  text-decoration: none;
}

.register-link:hover {
  text-decoration: underline;
}

.show-form-button {
  padding: 1rem;
  background-color: #007bff;
  border: none;
  color: white;
  border-radius: 5rem;
  width: 10rem;
  cursor: pointer;
  margin-right: 3rem;
  box-sizing: border-box;
}

.show-form-button:hover {
  background-color: #0056b3;
}

@media (max-width: 768px) {
  .container {
    flex-direction: column;
    padding: 1rem;
  }

  .description {
    max-width: none;
    text-align: center;
  }

  .description p {
    margin-left: 0;
  }

  .show-form-button {
    margin-right: 0;
  }
}
</style>
