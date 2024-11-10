<template>
  <div class="container-fluid">
    <nav class="navbar navbar-expand-lg navbar-light mb-4">
      <a class="navbar-brand" href="#">IITM Student Project Tracker</a>
      <div class="collapse navbar-collapse">
        <ul class="navbar-nav mr-auto">
          <li class="nav-item active">
            <a class="nav-link" @click="goToDashboard">Dashboard</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" @click="goToMyTeam">My Team</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" @click="goToInbox">Inbox</a>
          </li>
        </ul>
        <button class="btn btn-outline-danger my-2 my-sm-0 ml-auto" @click="logout">Logout</button>
      </div>
    </nav>
    <div class="main-content">
      <div class="card mb-4 shadow-lg">
        <div class="card-header">
          Project Submissions
        </div>
        <div class="card-body">
          <table class="table table-striped">
            <thead>
              <tr>
                <th>Date</th>
                <th>Title</th>
                <th>Status</th>
                <th>Feedback</th>
                <th>Actions</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="submission in submissions" :key="submission.id">
                <td>{{ submission.date }}</td>
                <td>{{ submission.title }}</td>
                <td>{{ submission.status }}</td>
                <td>{{ submission.feedback }}</td>
                <td>
                  <button class="btn btn-primary btn-sm" @click="upload(submission)">Upload</button>
                  <button class="btn btn-secondary btn-sm" @click="view(submission)">View</button>
                  <button class="btn btn-warning btn-sm" @click="review(submission)">Review</button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
      <div class="card shadow-lg">
        <div class="card-header">
          Progress
        </div>
        <div class="card-body">
          <div class="progress">
            <div class="progress-bar" role="progressbar" :style="{ width: progress + '%' }">
              {{ progress }}%
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      submissions: [
        { id: 1, date: '1/9/2024', title: 'Milestone 1', status: 'Completed', feedback: '⭐⭐⭐⭐⭐' },
        { id: 2, date: '15/9/2024', title: 'Milestone 2', status: 'Pending', feedback: '-' },
        { id: 3, date: '30/9/2024', title: 'Milestone 3', status: 'Pending', feedback: '-' },
      ],
      progress: 30, // Hardcoded progress value
    };
  },
  methods: {
    logout() {
      this.$router.push('/');
    },
    upload(submission) {
      alert(`Upload clicked for ${submission.title}`);
    },
    view(submission) {
      alert(`View clicked for ${submission.title}`);
    },
    review(submission) {
      alert(`Review clicked for ${submission.title}`);
    },
    goToMyTeam() {
      this.$router.push('/dashboard/myteam');
    },
    goToDashboard() {
      this.$router.push('/dashboard');
    },
    goToInbox() {
      this.$router.push('/dashboard/inbox');
    },
  },
};
</script>

<style scoped>
/* Full-Page Coverage */
html, body {
  height: 100%;
  margin: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

.container-fluid {
  padding: 0;
  height: 100%;
  background: linear-gradient(135deg, #e3f2fd, #c8e6c9); /* Soft blue to mint green gradient */
}

.main-content {
  padding: 30px;
  margin-top: 20px;
}

/* Navbar Styling */
.navbar {
  background: linear-gradient(90deg, #ffd54f, #ff8a80); /* Yellow to soft red gradient */
  padding: 15px 20px;
  border-radius: 10px;
}

.navbar-brand {
  font-weight: bold;
  color: #0d47a1; /* Dark blue */
}

.navbar-nav .nav-link {
  color: #00796b; /* Teal */
  font-weight: 500;
}

.navbar-nav .nav-link:hover {
  color: #d32f2f; /* Red hover */
}

.navbar .btn-outline-danger {
  color: #f44336; /* Red */
  border-color: #f44336;
}

.navbar .btn-outline-danger:hover {
  background-color: #f44336;
  color: white;
}

.navbar-collapse {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.navbar-nav {
  display: flex;
  gap: 15px;
}

.navbar-nav .nav-item {
  padding: 0 10px;
}

/* Card Styling */
.card {
  border-radius: 15px;
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
  background-color: #ffffff;
  border: none;
  margin-bottom: 30px;
  transition: transform 0.2s ease-in-out;
}

.card:hover {
  transform: translateY(-10px); /* Hover effect to lift the card */
}

.card-header {
  background: linear-gradient(90deg, #c8e6c9, #ffcc80); /* Mint green to light yellow */
  color: #0277bd; /* Darker blue */
  font-weight: bold;
  font-size: 1.1rem;
  border-radius: 10px 10px 0 0;
}

.card-body {
  padding: 25px;
  background-color: #fafafa;
}

/* Table Styling */
.table {
  width: 100%;
  margin-bottom: 20px;
  background-color: #ffffff;
}

.table-striped tbody tr:nth-of-type(odd) {
  background-color: #f1f8e9; /* Soft pale green */
}

.table th {
  background: #ffeb3b; /* Soft yellow */
  color: #0d47a1;
  font-weight: bold;
}

.table td {
  color: #004d40; /* Dark teal */
}

/* Button Styling Inside Table */
.btn-sm {
  padding: 6px 12px;
  font-size: 14px;
  border-radius: 25px;
  transition: transform 0.2s ease;
}

.btn-sm:hover {
  transform: scale(1.1); /* Slight scale on hover */
}

.btn-primary {
  background-color: #0288d1; /* Bright blue */
  border: none;
  color: white;
}

.btn-primary:hover {
  background-color: #0277bd; /* Darker blue */
}

.btn-secondary {
  background-color: #80cbc4; /* Soft mint */
  border: none;
  color: white;
}

.btn-secondary:hover {
  background-color: #4db6ac; /* Darker mint */
}

.btn-warning {
  background-color: #ffcc80; /* Soft yellow-orange */
  border: none;
  color: white;
}

.btn-warning:hover {
  background-color: #ffb74d; /* Darker yellow-orange */
}

/* Progress Bar Styling */
.progress {
  height: 20px;
  background-color: #f1f8e9; /* Light pastel green */
  border-radius: 10px;
}

.progress-bar {
  background-color: #388e3c; /* Dark green */
  text-align: center;
  color: white;
  border-radius: 10px;
}

/* Responsive Design */
@media (max-width: 767px) {
  .navbar-collapse {
    flex-direction: column;
    align-items: flex-start;
  }

  .navbar-nav {
    width: 100%;
    justify-content: space-evenly;
  }

  .card-header {
    font-size: 1rem;
  }
}
</style>
