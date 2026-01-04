# Movie-Details-Database
//index.html

<!DOCTYPE html>
<html>
<head>
    <title>Movie Archive Form</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<h2>Movie Archive Entry Form</h2>

<form action="insert.php" method="post">
    <label>Movie Name:</label>
    <input type="text" name="movie_name" required>

    <label>Movie Type:</label>
    <input type="text" name="movie_type" required>

    <label>Release Date:</label>
    <input type="date" name="release_date" required>

    <label>Producer Name:</label>
    <input type="text" name="producer_name" required>

    <label>Rotten Tomatoes Rating:</label>
    <input type="number" step="0.1" name="rating" required>

    <input type="submit" value="Save Movie">
</form>

</body>
</html> 



//style.css

body {
    font-family: Arial;
    background-color: #f2f2f2;
}

h2 {
    text-align: center;
}

form {
    width: 400px;
    margin: auto;
    background: white;
    padding: 20px;
}

label {
    display: block;
    margin-top: 10px;
}

input {
    width: 100%;
    padding: 6px;
}

input[type="submit"] {
    background: green;
    color: white;
    margin-top: 15px;
}


//db.php

<?php
$conn = mysqli_connect("localhost", "root", "", "movie_archive");

if (!$conn) {
    die("Connection failed");
}
?>


//insert.php

<?php
include 'db.php';

$movie_name = $_POST['movie_name'];
$movie_type = $_POST['movie_type'];
$release_date = $_POST['release_date'];
$producer_name = $_POST['producer_name'];
$rating = $_POST['rating'];

$sql = "INSERT INTO movies 
(movie_name, movie_type, release_date, producer_name, rating)
VALUES ('$movie_name', '$movie_type', '$release_date', '$producer_name', '$rating')";

if (mysqli_query($conn, $sql)) {
    echo "Movie stored successfully!";
} else {
    echo "Error!";
}
?>

