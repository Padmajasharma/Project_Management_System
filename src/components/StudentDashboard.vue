<template>
  <div class="container mt-5">
    <nav class="navbar navbar-expand-lg navbar-light bg-light mb-4">
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
        <button class="btn btn-outline-danger my-2 my-sm-0" @click="logout">Logout</button>
      </div>
    </nav>
    <div class="card mb-4">
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
    <div class="card">
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
    goToMyTeam(){
      this.$router.push('/dashboard/myteam');
    },
    goToDashboard(){
      this.$router.push('/dashboard');
    },
    goToInbox() {
      this.$router.push('/dashboard/inbox');
},

  },
};
</script>

<style scoped>
/* Container Styling */
.container {
  background-color: #e0f7e9;
  padding: 20px;
  border-radius: 8px;
}

/* Navbar Styling */
.navbar {
  background-color: #f8f9fa;
  border-bottom: 2px solid #ddd;
}

.navbar-brand {
  font-weight: bold;
  color: #007bff;
}

.nav-link {
  color: #555;
}

.nav-link:hover {
  color: #007bff;
}

.nav-item.active .nav-link {
  color: #007bff;
}

/* Button Styling */
.btn-outline-danger {
  border-color: #dc3545;
  color: #dc3545;
}

.btn-outline-danger:hover {
  background-color: #dc3545;
  color: #fff;
}

/* Card Styling */
.card {
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  margin-bottom: 20px;
}

.card-header {
  background-color: #f0f0f0;
  font-weight: bold;
  color: #333;
}

.card-body {
  padding: 20px;
}

/* Table Styling */
.table {
  width: 100%;
  margin-bottom: 20px;
  background-color: #fff;
}

.table-bordered th,
.table-bordered td {
  border: 1px solid #ddd;
  padding: 12px;
  text-align: center;
}

.table th {
  background-color: #f8f9fa;
  font-weight: bold;
}

/* Button Styling Inside Table */
.btn-sm {
  padding: 6px 12px;
  font-size: 14px;
  border-radius: 4px;
}

.btn-primary {
  background-color: #007bff;
  border: none;
  color: white;
}

.btn-primary:hover {
  background-color: #0056b3;
}

.btn-secondary {
  background-color: #6c757d;
  border: none;
  color: white;
}

.btn-secondary:hover {
  background-color: #5a6268;
}

.btn-warning {
  background-color: #ffc107;
  border: none;
  color: white;
}

.btn-warning:hover {
  background-color: #e0a800;
}

/* Progress Bar Styling */
.progress {
  height: 20px;
  background-color: #f1f1f1;
  border-radius: 10px;
}

.progress-bar {
  background-color: #4caf50;
  text-align: center;
  color: white;
  border-radius: 10px;
}
</style>

