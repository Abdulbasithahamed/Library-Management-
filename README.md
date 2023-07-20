# Library-Management-
<!DOCTYPE html>
<html>
<head>
  <title>Library Management Page</title>
  <style>
    table {
      width: 100%;
      border-collapse: collapse;
    }

    th, td {
      border: 1px solid black;
      padding: 8px;
    }

    th {
      background-color: #f2f2f2;
    }
  </style>
</head>
<body>
  <h1>Library Management</h1>

  <label for="searchTitle">Search by Title:</label>
  <input type="text" id="searchTitle" onkeyup="filterBooks()" placeholder="Enter title..">

  <label for="searchAuthor">Search by Author:</label>
  <input type="text" id="searchAuthor" onkeyup="filterBooks()" placeholder="Enter author..">

  <label for="searchSubject">Search by Subject:</label>
  <input type="text" id="searchSubject" onkeyup="filterBooks()" placeholder="Enter subject..">

  <label for="searchPublishDate">Search by Publish Date:</label>
  <input type="date" id="searchPublishDate" oninput="filterBooks()">

  <table id="libraryTable">
    <tr>
      <th>Title</th>
      <th>Author</th>
      <th>Subject</th>
      <th>Publish Date</th>
    </tr>
    <tr>
      <td>Book 1</td>
      <td>Author 1</td>
      <td>Subject 1</td>
      <td>2021-01-15</td>
    </tr>
    <tr>
      <td>Book 2</td>
      <td>Author 2</td>
      <td>Subject 2</td>
      <td>2022-05-20</td>
    </tr>
    <!-- Add more book entries here -->
  </table>

  <script>
    function filterBooks() {
      const inputTitle = document.getElementById("searchTitle").value.toUpperCase();
      const inputAuthor = document.getElementById("searchAuthor").value.toUpperCase();
      const inputSubject = document.getElementById("searchSubject").value.toUpperCase();
      const inputPublishDate = document.getElementById("searchPublishDate").value;

      const table = document.getElementById("libraryTable");
      const rows = table.getElementsByTagName("tr");

      for (let i = 1; i < rows.length; i++) {
        const title = rows[i].getElementsByTagName("td")[0].innerText.toUpperCase();
        const author = rows[i].getElementsByTagName("td")[1].innerText.toUpperCase();
        const subject = rows[i].getElementsByTagName("td")[2].innerText.toUpperCase();
        const publishDate = rows[i].getElementsByTagName("td")[3].innerText;

        const titleMatch = title.includes(inputTitle);
        const authorMatch = author.includes(inputAuthor);
        const subjectMatch = subject.includes(inputSubject);
        const publishDateMatch = inputPublishDate === "" || publishDate === inputPublishDate;

        if (titleMatch && authorMatch && subjectMatch && publishDateMatch) {
          rows[i].style.display = "";
        } else {
          rows[i].style.display = "none";
        }
      }
    }
  </script>
</body>
</html>
