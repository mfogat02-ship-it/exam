async function fetchUsers() {
  const url = "https://jsonplaceholder.typicode.com/users";

  try {
    // Make the request
    const response = await fetch(url);

    // Check if the response is OK
    if (!response.ok) {
      throw new Error(`HTTP error! Status: ${response.status}`);
    }

    // Convert response to JSON
    const data = await response.json();

    // Display data
    displayUsers(data);

  } catch (error) {
    console.error("Error fetching data:", error);
  }
}

// Function to display users in the DOM
function displayUsers(users) {
  const container = document.getElementById("user-container");

  users.forEach(user => {
    const div = document.createElement("div");
    div.innerHTML = `
      <h3>${user.name}</h3>
      <p>Email: ${user.email}</p>
      <p>City: ${user.address.city}</p>
    `;
    container.appendChild(div);
  });
}

// Call the function
fetchUsers();
Minimal HTML to display results
<!DOCTYPE html>
<html>
<head>
  <title>Fetch API Example</title>
</head>
<body>
  <h1>User List</h1>
  <div id="user-container"></div>

  <script src="script.js"></script>
</body>
</html>
