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
        <button class="btn btn-outline-dark my-2 my-sm-0 ml-auto" @click="logout">Logout</button>
      </div>
    </nav>
    <div class="main-content">
      <div class="card mb-4 shadow-sm">
        <div class="card-header">
          Project Submissions
        </div>
        <div class="card-body">
          <table class="table table-bordered">
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
      <div class="card shadow-sm">
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
  background-color: #f5f5f5; /* Light neutral background */
}

.main-content {
  padding: 30px;
  margin-top: 20px;
}

/* Navbar Styling */
.navbar {
  background-color: #ffffff; /* Clean white background */
  padding: 15px 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.navbar-brand {
  font-weight: bold;
  color: #333; /* Dark grey for better contrast */
}

.navbar-nav .nav-link {
  color: #555; /* Soft grey for nav items */
  font-weight: 500;
}

.navbar-nav .nav-link:hover {
  color: #007bff; /* Soft blue on hover */
}

.navbar .btn-outline-dark {
  color: #333;
  border-color: #333;
}

.navbar .btn-outline-dark:hover {
  background-color: #333;
  color: white;
}

/* Card Styling */
.card {
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  background-color: #ffffff;
  border: none;
  margin-bottom: 30px;
}

.card-header {
  background-color: #f1f1f1; /* Very light grey */
  color: #333; /* Dark grey */
  font-weight: bold;
  font-size: 1.1rem;
}

.card-body {
  padding: 25px;
  background-color: #fafafa; /* Light soft background */
}

/* Table Styling */
.table {
  width: 100%;
  margin-bottom: 20px;
  background-color: #ffffff;
}

.table-bordered {
  border: 1px solid #e0e0e0;
}

.table-bordered th, .table-bordered td {
  border: 1px solid #e0e0e0;
  padding: 12px 15px;
}

.table th {
  background-color: #f8f9fa; /* Very light grey */
  color: #333; /* Dark grey */
  font-weight: bold;
}

.table td {
  color: #555; /* Soft grey text */
}

/* Button Styling Inside Table */
.btn-sm {
  padding: 6px 12px;
  font-size: 14px;
  border-radius: 25px;
  transition: transform 0.2s ease;
}

.btn-sm:hover {
  transform: scale(1.05); /* Slight scale on hover */
}

.btn-primary {
  background-color: #007bff; /* Soft blue */
  border: none;
  color: white;
}

.btn-primary:hover {
  background-color: #0056b3; /* Darker blue */
}

.btn-secondary {
  background-color: #6c757d; /* Soft grey */
  border: none;
  color: white;
}

.btn-secondary:hover {
  background-color: #5a6268; /* Darker grey */
}

.btn-warning {
  background-color: #ffc107; /* Soft yellow */
  border: none;
  color: white;
}

.btn-warning:hover {
  background-color: #e0a800; /* Darker yellow */
}

/* Progress Bar Styling */
.progress {
  height: 20px;
  background-color: #e9ecef; /* Light grey */
  border-radius: 10px;
}

.progress-bar {
  background-color: #28a745; /* Green for progress */
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
