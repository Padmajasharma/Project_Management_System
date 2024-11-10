<style scoped>
/* Full-Page Coverage */
html, body {
  height: 100%;
  margin: 0;
}

.container {
  background-color: #f9f9f9; /* Pastel background */
  min-height: 100vh; /* Full-page height */
  padding: 40px 20px;
}

/* Navbar Styling */
.navbar {
  background-color: #f0f4f8; /* Light pastel blue */
  border-bottom: 2px solid #ddd;
  padding: 10px 20px;
}

.navbar-brand {
  font-weight: bold;
  color: #5c6bc0; /* Soft blue */
}

.navbar-nav .nav-link {
  color: #888;
}

.navbar-nav .nav-link:hover {
  color: #5c6bc0;
}

.navbar-nav .nav-item.active .nav-link {
  color: #5c6bc0;
}

.navbar .btn-outline-danger {
  color: #ff6f61; /* Soft coral color */
  border-color: #ff6f61;
}

.navbar .btn-outline-danger:hover {
  background-color: #ff6f61;
  color: #fff;
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
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  background-color: #ffffff; /* Light pastel card background */
  border: none;
  margin-bottom: 30px;
}

.card-header {
  background-color: #f4f9f9; /* Light pastel gray */
  color: #333;
  font-weight: bold;
  font-size: 1.1rem;
}

.card-body {
  padding: 20px;
  background-color: #fafafa; /* Very light pastel background */
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
  background-color: #f0f4f8; /* Soft pastel blue */
  color: #5c6bc0;
  font-weight: bold;
}

/* Button Styling Inside Table */
.btn-sm {
  padding: 6px 12px;
  font-size: 14px;
  border-radius: 4px;
}

.btn-primary {
  background-color: #5c6bc0; /* Soft blue */
  border: none;
  color: white;
}

.btn-primary:hover {
  background-color: #3e4f8d; /* Darker blue on hover */
}

.btn-secondary {
  background-color: #b0bec5; /* Light grayish blue */
  border: none;
  color: white;
}

.btn-secondary:hover {
  background-color: #90a4ae; /* Slightly darker on hover */
}

.btn-warning {
  background-color: #ffb74d; /* Soft orange */
  border: none;
  color: white;
}

.btn-warning:hover {
  background-color: #ffa726; /* Slightly darker on hover */
}

/* Progress Bar Styling */
.progress {
  height: 20px;
  background-color: #f1f1f1;
  border-radius: 10px;
}

.progress-bar {
  background-color: #4caf50; /* Greenish pastel */
  text-align: center;
  color: white;
  border-radius: 10px;
}

/* Make buttons smaller in the table */
.card-body .btn {
  font-size: 14px;
}

/* Responsive: ensure the navbar and container are properly aligned */
@media (max-width: 767px) {
  .navbar-collapse {
    flex-direction: column;
    align-items: flex-start;
  }

  .navbar-nav {
    width: 100%;
    justify-content: space-evenly;
  }
}
</style>
